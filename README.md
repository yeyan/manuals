## How to remove RSA private key passphrase

#### Backup ssh keys and configuration files

***This is very important***

```bash
cp -r ~/.ssh ~/.ssh_backup
```

#### Remove the password phrase

It will require the password.

```bash
openssl rsa -in ~/.ssh/id_rsa -out ~/.ssh/id_rsa_new
chmod 400 ~/.ssh/id_rsa_new
```

#### Test the new key

It shouldn't require the password.

```bash
ssh -i ~/.ssh/id_rsa_new <some_host>
```

Successfully login without password means this new private key is useable.

#### Remove it with the old private key

```bash
rm ~/.ssh/id_rsa
cp ~/.ssh/id_rsa_new ~/.ssh/id_rsa
```

After this step we should good to go with the rsa private passphrase free.
