# Password Cracking Lab – Cyber Security Mini Project

## Overview
This is a simple project where I tried to crack a weak password using a wordlist and a popular password cracking tool called John the Ripper. The goal was to understand how weak passwords can be guessed easily if they're not strong enough.

## Tools I Used
- Terminal on macOS
- John the Ripper (installed using Homebrew)
- OpenSSL (already available on macOS)
- A custom wordlist I created

---

## Steps I Followed

### 1. Installed Homebrew and John the Ripper

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"  
# This installs Homebrew (a package manager for macOS)

/opt/homebrew/bin/brew shellenv  
# This sets up Homebrew’s environment variables

echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile  
# I added Homebrew to my shell profile so it's always available in new Terminal windows

eval "$(/opt/homebrew/bin/brew shellenv)"  
# Applied the above shell configuration instantly

brew install john  
# Installed John the Ripper using Homebrew
echo "user:$(openssl passwd -1 password123)" > hashfile.txt  
# I created a test user "user" with a hashed version of the password "password123"
# and saved it into a file named hashfile.txt
echo "password123" > wordlist.txt  
# I created a small wordlist with the password I wanted to try
john --wordlist=wordlist.txt hashfile.txt  
# This ran the password cracker using my custom wordlist and hashed file
john --show hashfile.txt  
# This showed the actual cracked password from the hash
---



## ✅ Output

```
user:password123

1 password hash cracked, 0 left
```

