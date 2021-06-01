Title: Release Setup

These setup steps only need to be performed on a particular machine once.
*Note*: Developers using Linux workstations can skip over the references to
[Cygwin][]. If using Windows, install cygwin, including `Utils/gnupg` and
`Net/openssh` packages.

<a name="ReleaseSetup-CreateandinstallaSSHkey"></a>
### Create and install a SSH key

1. Open a shell window.	If using Windows, open a cygwin window.
1. Use `ssh-keygen` to create an SSH key.
    *Note*: Follow the latest steps and guides on the ASF website at
    <http://www.apache.org/dev/openpgp.html#generate-key>
    as you need to disable using SHA1 and new keys should be 4096 bits.

```sh
        ssh-keygen -t dsa -b 4096
```

    Program defaults should be fine.  No passphrase is required for the `ssh`
    key generation.  The keys will be saved in `~/.ssh/id_dsa` (private) and
    `~/.ssh/id_dsa.pub` (public).

    *See [Authenticating By Public Key (OpenSSH)](http://www.networknewz.com/networknewz-10-20030707AuthenticatingbyPublicKeyOpenSSH.html)
    for a good description on why and how to perform this task.*

1. `scpl` your SSH public key `~/.ssh/id_dsa.pub` created in last step to
 `~/id_dsa.pub` on `people.apache.org`:

```sh
        cd ~/.ssh
        scp id_dsa.pub <your userid>@people.apache.org:id_dsa.pub
```

    You will be prompted for your password.

1. Use `ssh` to log into `people.apache.org`:

```sh
        cd ~
        ssh <your userid>@people.apache.org
```

    At this point, you will still be prompted for your password.

1. Create a `.ssh` folder in your home directory (`~`) on `people.apache.org` and
    change its file mode to `700`
    (owner read/write/execute, no permissions granted to anyone else):

```sh
        mkdir ~/.ssh
        chmod 700 ~/.ssh
```

1. Move or append `~/id_dsa.pub` to `~/.ssh/authorized_keys` and change its file
mode to `600` (owner read/write, no permissions granted to anyone else):

```sh
        mv ~/id_dsa.pub ~/.ssh/authorized_keys
        chmod 600 ~/.ssh/authorized_keys
```

    Each public key in the `authorized_keys` file spans only one line, e.g.:

```text
        ssh-dss AAAAB3NzaC1kc3MAAA ..... agBmmfZ9uAbSqA==dsa-key-20071107
```

    (any line with `'#'` in the first column is a comment line)

1. Exit out of this `ssh` session.
1. Start a new `ssh` session.  No login should be required this time due to
    the private key on your local box matching up with the public key
    in your home directory (`~/.ssh`):

```sh
        ssh $  {USER}@people.apache.org
```

    If you are still prompted for a password, then you have not set up the
    keys properly. Review the steps above and ensure that all of the steps
    were followed properly.  Or, maybe the instructions are still not quite
    right and they still need some adjusting.  In that case, please update the
    instructions accordingly. :-)

<a name="ReleaseSetup-CreateaGPGkey"></a>
### Create a GPG key

1. Open a shell window.	If using Windows, open a cygwin window.
1. Generate a key-pair with `gpg`, using default key kind ("DSA and Elgamal")
and ELG-E keys size (2048).

```sh
        gpg --gen-key
```

    The program's default values should be fine. For the "Real Name" enter
    your full name (ie. Stan Programmer).  For the "e-mail address" enter your
    apache address (ie. sprogrammer@apache.org).  You will also be required to
    enter a "passphrase" for the GPG key generation.  Keep track of this as you
    will need this for the Release processing.

    *The generated keys are stored in `$HOME/.gnupg` or `%HOME%\Application
Data\gnupg` directory.*
    *Save the content in this directory to a safe medium. This contains your
private key used to sign all the BVal release materials.*

1. Back up your cygwin home directory to some other medium.
1. Add your public key to <https://svn.apache.org/repos/asf/bval/KEYS>
 and <http://www.apache.org/dist/bval/KEYS>. See the commands
described at the beginning of this KEYS file to perform this task. The gpg
key-pair is used to sign the published artifacts for the BVAL releases. 

```sh
        gpg --list-sigs <Real Name> && gpg --armor -- export <Real Name>
```

    *The <https://svn.apache.org/repos/asf/bval/KEYS>
    file is updated via normal svn commit procedures.  The one at
    <http://www.apache.org/dist/bval/KEYS> must be manually updated from svn.*

1. Submit your public key to a key server, e.g. <http://pgp.surfnet.nl:11371/>
 or <http://pgp.mit.edu/>.

1. Following the instructions in <http://people.apache.org/~henkp/trust/> and
 ask multiple (at least 3) current Apache committers to sign your public key.

<a name="ReleaseSetup-UpdateMavensettingsforourservers"></a>
### Update Maven settings for our servers

Create a `settings.xml` under `.m2`:

```xml
    <settings xmlns="http://maven.apache.org/POM/4.0.0"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/settings-1.0.0.xsd">
      <servers>
        <!-- SCP settings for people.apache.org -->
        <server>
          <id>people.apache.org</id>
          <username>$USERNAME</username>
          <privateKey>$PATH_TO_PRIVATE_KEY</privateKey>
          <passphrase>$SSH_PASSPHRASE</passphrase>
          <directoryPermissions>775</directoryPermissions>
          <filePermissions>644</filePermissions>
          <!-- following is only for Windows only
          <configuration>
            <sshExecutable>plink</sshExecutable>
            <scpExecutable>pscp</scpExecutable>
            <scpArgs>-2Bp</scpArgs>
            <sshArgs>-2</sshArgs>
          </configuration>
          -->
        </server>
        <!-- ASF Nexus settings -->
        <server>
          <id>apache.snapshots.https</id>
          <username>$USERNAME</username>
          <password>$APACHE_LDAP_PWD</password>
        </server>
        <server>
          <id>apache.releases.https</id>
          <username>$USERNAME</username>
          <password>$APACHE_LDAP_PWD</password>
        </server>
      </servers>	  
    </settings>
```

Notes:

* *`$USERNAME` is the remote username on `people.apache.org`,
  not necessarily your local userid.*
* *`$PATH_TO_PRIVATE_KEY` is the path to the private `ssh` key generated, e.g.
`/home/yourLocalUserId/.ssh/id_dsa`.  For cygwin users,
you will need to enter the full cygwin path:
`/cygdrive/c/cygwin/home/yourLocalUserId/.ssh/id_dsa`.*
* *`$SSH_PASSPHRASE` for the supplied `$PATH_TO_PRIVATE_KEY`. If you
don't use this in your `settings.xml` file, then you will be prompted for it
during the Release processing.*
* *`$APACHE_LDAP_PWD` is your Apache LDAP password, which is shared
between SVN and password login for `people.apache.org`.*

[cygwin]: http://www.cygwin.com/
