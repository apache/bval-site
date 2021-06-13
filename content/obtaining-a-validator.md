Title: Obtaining a validator

To obtain a `Validator`, you must first create a `ValidatorFactory`. If there
is only one Bean Validation implementation in your classpath, you can use:

```java
    ValidatorFactory vf = Validation.buildDefaultValidatorFactory();
```

to obtain the factory. If there are various implementations in the
classpath, or you want to be sure you are using Apache BVal, you can
use:

```java
    ValidatorFactory avf =
        Validation.byProvider(ApacheValidationProvider.class).configure().buildValidatorFactory();
```

You should usually not instantiate more than one factory; factory creation is a
costly process. Also, the factory also acts as a cache for the available
validation constraints.

Once you have a ValidatorFactory, obtaining a validator just requires you
to call `ValidatorFactory#getValidator()`. The validator implementation
is thread-safe, so you can choose to re-use a single instance of it in all
your code or create validators on demand: both options should
perform equally well.

Below is an example that will create a singleton `ValidatorFactory` and will
let you obtain `Validator`s from it:

```java
    public enum MyValidatorFactory  {

        SINGLE_INSTANCE  {

            ValidatorFactory avf =
                Validation.byProvider(ApacheValidationProvider.class).configure().buildValidatorFactory();

            @Override
            public Validator getValidator()  {
                return avf.getValidator();
            }

        };

        public abstract Validator getValidator(); 
    }
```

Using the above class, obtaining a `Validator` just requires you to call:

```java
    MyValidatorFactory.SINGLE_INSTANCE.getValidator()
```

<a name="Obtainingavalidator-UsingSpring"></a>
### Using [The Spring Framework][spring]

If you are using Spring, you can easily inject `Validator`s into your beans.
Simply configure the factory in your `ApplicationContext` by adding:

```xml
    <!-- Validator bean -->
    <bean id="validator"
        class="org.springframework.validation.beanvalidation.LocalValidatorFactoryBean">
        <property name="providerClass"
            value="org.apache.bval.jsr303.ApacheValidationProvider" />
    </bean>
```

And Spring will be able to inject `Validator`s and the `ValidatorFactory` into
your beans.

<a name="Obtainingavalidator-UsingGoogleGuice"></a>
### Using Google Guice

Apache BVal provides the `bval-guice` module that simplifies
integration with [Google Guice][guice]. That module has multiple purposes, such:

* bootstrap Apache BVal using Google Guice;
* obtain `javax.validation.ConstraintValidator` instances using the Google
Guice `Injector` to easily support DI;
* easily inject the `javax.validation.Validator` reference into components
that require it;
* easily intercept methods and validate method arguments.

First of all, users have to add the `bval-guice` module in the classpath;
[Apache Maven][maven] users can easily include it just by adding the following
dependency in the POM:

```xml
    <dependency>
      <groupId>org.apache.bval</groupId>
      <artifactId>bval-guice</artifactId>
      <version>0.3-incubating</version>
    </dependency>
```

Let's have a look at the features:

<a name="Obtainingavalidator-ApacheBValbootstrapping"></a>
##### Bootstrapping Apache BVal

Simply, the `org.apache.bval.guice.ValidationModule` is the Google
Guice module that bootstraps Apache BVal. All users have to do is add
this module when creating the Google Guice `Injector`:

```java
    import com.google.inject.Guice;
    import com.google.inject.Injector;

    import org.apache.bval.guice.ValidationModule;

    Injector injector = Guice.createInjector([...](....html),
        new ValidationModule(), [...]
    );
```

##### Obtain `javax.validation.ConstraintValidator` instances
    
Users can now implement `javax.validation.ConstraintValidator` classes that
require _Dependency Injection_ by Google Guice:

```java
    import javax.validation.ConstraintValidator;

    public class MyCustomValidator implements ConstraintValidator<MyAssert, MyType>  {

        private final MyExternalService service;

        @Inject
        public MyCustomValidator(MyExternalService service)  {
    	this.service = service;
        }

        public void initialize(MyAssert annotation)  {
    	// do something
        }

        public boolean isValid(MyType value, ConstraintValidatorContext context)  {
            return value == null || this.service.doSomething(value);
        }
    }
```

Don't forget to bind the `MyExternalService` class in the Google Guice
`Binder`!!!

<a name="Obtainingavalidator-Injectthe_javax.validation.Validator_reference"></a>
##### Inject the `javax.validation.Validator` reference

Clients can easily inject `javax.validation.Validator` instances into
their custom components just marking it using the Google Guice `@Inject`
annotation:

```java
    import javax.validation.Validator;

    public class MyValidatorClient  {

        @Inject
        private Validator validator;

        public void setValidator(Validator validator)  {
	    this.validator = validator;
        }

        // ...

    }
```

When obtaining `MyValidatorClient` instances from the `Injector`, the
`javax.validation.Validator` will be automagically bound.

##### Intercept methods and validate method arguments
    
Taking advantage of the Apache BVal extension to validate method
arguments, the `bval-guice` module comes with an _AOP_ interceptor,
automatically initialized in the `org.apache.bval.guice.ValidationModule`,
that facilitates the validation of method arguments.

All users have to do is annotate interested methods with
`org.apache.bval.guice.Validate` annotation, then annotate arguments with
constraints, as follows below:
    
```java
    import javax.validation.constraints.NotNull;
    import javax.validation.constraints.Size;
    
    import org.apache.bval.guice.Validate;
    
    public class MyService  {
    
        @Validate(
    	    groups =  { MyGroup.class },
    	    validateReturnedValue = true
        )
        public Country insertCountry(@NotNull(groups =  { MyGroup.class })
    	    String name,
    	    @NotNull(groups =  { MyGroup.class })
    	    @Size(max = 2, groups =  { MyGroup.class, MyOtherGroup.class })
    	    String iso2Code,
    	    @NotNull(groups =  { MyGroup.class })
    	    @Size(max = 3, groups =  { MyGroup.class, MyOtherGroup.class })
    	    String iso3Code)  {

    	    return ...;
        }

    }
```

The `bval-guice @Validate` annotation supports 2 values:

* `groups` Class array, `  {}` by default, that specifies the groups to be validated;
* `validateReturnedValue` flag, `false` by default, indicating whether
the method's return value should be validated.

<a name="Obtainingavalidator-UsingCDI"></a>
### Using CDI

Bean Validation integration with [CDI][] is provided by:

* The Bean Validation integration module of [MyFaces CODI][]
* [Seam Validation Module][]

[guice]: http://code.google.com/p/google-guice/
[spring]: http://www.springsource.org
[maven]: http://maven.apache.org
[cdi]: http://jcp.org/en/jsr/summary?id=299
[MyFaces CODI]: http://myfaces.apache.org/extensions/cdi/index.html
[seam validation module]: http://seamframework.org/Seam3/ValidationModule
