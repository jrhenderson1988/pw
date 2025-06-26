# pw

A simple, local-only password manager, that uses GPG.

## Installation

1. Clone this repository

2. Make the `pw` script executable (if it's not already)

   ```bash
   $ chmod +x pw
    ```

3. Make `pw` accessible on your PATH by either:
   - Making a symlink somewhere on your PATH that points to `pw` in this repository. For example:

        ```bash
        # assuming ~/bin is on your PATH
        $ ln -s ~/path/to/pw ~/bin/pw
        ```

   - Adding this repository's location to your `PATH` environment variable. For example, in ZSH, add the following to `~/.zshrc`:

        ```bash
        # make sure to restart your terminal or run source ~/.zshrc afterwards
        export PATH="$PATH:/path/to/pw"
        ```

## Setup

To set up `pw`, run `pw init`. If you run `pw` without first initialising, you'll be prompted to run `pw init`.

Enter your email address that you want to associate with your identity and key and hit enter. You'll be prompted for a passphrase for your GPG keypair. It is **strongly** recommended to provide a passphrase. If you don't use one, your passwords would be accessible by anyone with access to your computer.

A GPG keypair that does not expire will be generated and an `identity` file containing entered your email address will be placed under `~/.pw/`

If you prefer a manual setup, you can:

Create a GPG keypair (4096-bit RSA is recommended - choose a strong passphrase):

```bash
$ gpg --full-generate-key
```

And then create an identity file containing your email address (the same one you used for your keypair):

```bash
$ mkdir -p ~/.pw
$ echo "you@domain.com" > ~/.pw/identity
```

## Usage

| Command          | Comments                                                                                                   |
|------------------|------------------------------------------------------------------------------------------------------------|
| `pw init`        | Initialise `pw` for the first time                                                                         |
| `pw ls`          | List your passwords                                                                                        |
| `pw add <name>`  | Add a password named `<name>` - will launch `vim` and you should enter your password and save the file     |
| `pw gen`         | Generate a random password and output to stdout                                                            |
| `pw gencp`       | Generate a random password and copy it to the clipboard                                                    |
| `pw show <name>` | Show a password. You will be prompted for your passphrase and the password will be printed to stdout       |
| `pw cp <name>`   | Copy a password to the clipboard. You will be prompted for your passphrase                                 |
| `pw rm <name>`   | Delete a password. You will be asked to confirm by entering the text `DELETE`. This action is irreversible |

