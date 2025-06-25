# pw

A simple, local-only password manager, that uses GPG.

## Installation

Add this repository to your PATH by adding the following to `~/.zshrc`:

```bash
PATH="$PATH:/path/to/pw"
```

Make sure you restart your terminal or `source` your .zshrc

```bash
source ~/.zshrc
```

## Setup

Create a `recipient` file with your email address in it

```bash
$ mkdir -p ~/.pw
$ echo "you@domain.com" > ~/.pw/recipient
```

Create your GPG keypair. Make sure that you use the same email that you wrote to your `recipient` 
file as the email for the GPG key:

```bash
$ gpg --full-generate-key
```

### Recommended settings:
- RSA
- 4096 bits
- A strong passphrase (you'll use this to unlock your keypair when accessing passwords)

## Usage

| Command          | Comments                                                                                                   |
|------------------|------------------------------------------------------------------------------------------------------------|
| `pw ls`          | List your passwords                                                                                        |
| `pw add <name>`  | Add a password named `<name>` - will launch `vim` and you should enter your password and save the file     |
| `pw gen`         | Generate a random password and output to stdout                                                            |
| `pw gencp`       | Generate a random password and copy it to the clipboard                                                    |
| `pw show <name>` | Show a password. You will be prompted for your passphrase and the password will be printed to stdout       |
| `pw cp <name>`   | Copy a password to the clipboard. You will be prompted for your passphrase                                 |
| `pw rm <name>`   | Delete a password. You will be asked to confirm by entering the text `DELETE`. This action is irreversible |

