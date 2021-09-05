# SSH COnfiguracion

Para utilizar una cuenta de Github desde nuestra local machine es necesario
que github compruebe que se es el dueño de dicha cuenta, para eso utilizamos las SSH KEYs

## Comandos SSH Key en la terminal de linux

ssh-keygen -t rsa -b 4096 -C "email@addres.com"

### -t public key algorithm for authentication keys

### ### -b Key size (4096)

determina el tamañoo de la clave.

### -f nombre y hubicaciondel archivo de clave genrado

si se desea se puede esṕesificar el archivo donde se guardará la clave SSH.

### Algoritmos usados para generar la clave.

    rsa - an old algorithm based on the difficulty of factoring large numbers. A key size of at least 2048 bits is recommended for RSA; 4096 bits is better. RSA is getting old and significant advances are being made in factoring. Choosing a different algorithm may be advisable. It is quite possible the RSA algorithm will become practically breakable in the foreseeable future. All SSH clients support this algorithm.

    dsa - an old US government Digital Signature Algorithm. It is based on the difficulty of computing discrete logarithms. A key size of 1024 would normally be used with it. DSA in its original form is no longer recommended.

    ecdsa - a new Digital Signature Algorithm standarized by the US government, using elliptic curves. This is probably a good algorithm for current applications. Only three key sizes are supported: 256, 384, and 521 (sic!) bits. We would recommend always using it with 521 bits, since the keys are still small and probably more secure than the smaller keys (even though they should be safe as well). Most SSH clients now support this algorithm.

    ed25519 - this is a new algorithm added in OpenSSH. Support for it in clients is not yet universal. Thus its use in general purpose applications may not yet be advisable.

## Copiar la Public Key al servidor.

ssh-copy-id -i ~/.ssh/tatu-key-ecdsa user@host

## Adding your SSH key to the ssh-agent
Before adding a new SSH key to the ssh-agent to manage your keys, you should have checked for existing SSH keys and generated a new SSH key.

    Start the ssh-agent in the background.

    $ eval "$(ssh-agent -s)"
    > Agent pid 59566

    Depending on your environment, you may need to use a different command. For example, you may need to use root access by running sudo -s -H before starting the ssh-agent, or you may need to use exec ssh-agent bash or exec ssh-agent zsh to run the ssh-agent.

    Add your SSH private key to the ssh-agent. If you created your key with a different name, or if you are adding an existing key that has a different name, replace id_ed25519 in the command with the name of your private key file.

    $ ssh-add ~/.ssh/id_ed25519

    Add the SSH key to your account on GitHub. For more information, see "Adding a new SSH key to your GitHub account."



# Command and Option Summary

Here's a summary of commonly used options to the keygen tool:

-b “Bits” This option specifies the number of bits in the key. The regulations that govern the use case for SSH may require a specific key length to be used. In general, 2048 bits is considered to be sufficient for RSA keys.

-e “Export” This option allows reformatting of existing keys between the OpenSSH key file format and the format documented in RFC 4716, “SSH Public Key File Format”.

-p “Change the passphrase” This option allows changing the passphrase of a private key file with [-P old_passphrase] and [-N new_passphrase], [-f keyfile].

-t “Type” This option specifies the type of key to be created. Commonly used values are: - rsa for RSA keys - dsa for DSA keys - ecdsa for elliptic curve DSA keys

-i "Input" When ssh-keygen is required to access an existing key, this option designates the file.

-f "File" Specifies name of the file in which to store the created key.

-N "New" Provides a new passphrase for the key.

-P "Passphrase" Provides the (old) passphrase when reading a key.

-c "Comment" Changes the comment for a keyfile.

-p Change the passphrase of a private key file.

-q Silence ssh-keygen.

-v Verbose mode.

-l "Fingerprint" Print the fingerprint of the specified public key.

-B "Bubble babble" Shows a "bubble babble" (Tectia format) fingerprint of a keyfile.

-F Search for a specified hostname in a known_hosts file.

-R Remove all keys belonging to a hostname from a known_hosts file.

-y Read a private OpenSSH format file and print an OpenSSH public key to stdout.
