## How to remove RSA private key passphrase

#### Backup ssh keys and configuration files

This is very important, **DO NOT PROCEED** without this step.

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

Enjoy your passphrase free private.
