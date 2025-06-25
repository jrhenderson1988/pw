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

Recommended settings:
- RSA
- 4096 bits
- A strong passphrase (you'll use this to unlock your keypair when accessing passwords)