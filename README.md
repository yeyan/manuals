## How to remove RSA private key passphrase

1. Backup ssh keys and configuration files

** this is very important **

```bash
cd ~/.ssh
7z a backup.zip *
7z l backup.zip
```

If you don't have 7z installed:

```bash
brew install p7zip
```
 
2. Remove the password phrase

It will require the password.

```bash
openssl rsa -in ~/.ssh/id_rsa -out ~/.ssh/id_rsa_new
chmod 400 ~/.ssh/id_rsa_new
```

3. Test the new key

It shouldn't require the password.

```bash
ssh -i ~/.ssh/id_rsa_new <some_host>
```

Successfully login without password means this new private key is useable.

4. Remove it with the old private key

```bash
cp ~/.ssh/id_rsa ~/.ssh/id_rsa.backup
rm ~/.ssh/id_rsa
cp ~/.ssh/id_rsa_new ~/.ssh/id_rsa
```

It never a bad thing if we have too many backups.

After this step we should good to go with the rsa private passphrase free.
