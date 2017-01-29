# NLNOG Infrastructure

## Getting the ansible roles
`ansible-galaxy install -f -r requirements.yml`

## Working with encrypted variables
Encrypted variables are saved in secret_vars/$HOSTNAME.yml, the playbooks/load_vars.yml
playbook should be included in every playbook to grab these encrypted variables.

These encrypted files should automatically be decrypted.

### changing the gpg keys used to encrypt the vault password
`gpg -d vault_passphrase.gpg | gpg -e --trust-model always -r "KEYID1" -r "KEYID2" (etc..) -o vault_passphrase.gpg.new; mv vault_passphrase.gpg.new vault_passphrase.gpg`

### Adding an encrypted file
`ansible-vault create secret_vars/$HOSTNAME.yml`
