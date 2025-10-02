# Adapted from https://github.com/Simporter/get-env-file-from-vault

## Get env-file from Hashicorp Vault GitHub Action

Simple action to get env file from HashiCorp Vault™.

## Example Usage

```yaml
jobs:
  build:
    # ...
    steps:
      # ...
      - name: Get env file
        uses: https://git.trez.wtf/Trez/hc-vault-env@main
        with:
          HC_VAULT_VERSION: "1.20.4"
          HC_VAULT_ADDR: https://vault.mycompany.com:8200
          HC_VAULT_USERNAME: ${{ secrets.HC_VAULT_USERNAME }}
          HC_VAULT_PASSWORD: ${{ secrets.HC_VAULT_PASSWORD }}
          HC_VAULT_SECRETS_PATH: ${{ secrets.HC_VAULT_SECRETS_PATH }}
      # ...
```

will get all the secrets from `kv` storage from `HC_VAULT_SECRETS_PATH` and put it in a `.env`

## Authentication method

Currently, only `userpass` login method is implemented. `HC_VAULT_USERNAME` and `HC_VAULT_PASSWORD` to authenticate with Vault.

## Reference

Here are all the inputs available through `with`:

| Input                   | Description                              | Default | Required |
| ----------------------- | ---------------------------------------- | ------- | -------- |
| `HC_VAULT_VERSION`      | Vault version                            |         | ✔        |
| `HC_VAULT_ADDR`         | Vault url                                |         | ✔        |
| `HC_VAULT_USERNAME`     | Vault login username for `userpass` auth |         | ✔        |
| `HC_VAULT_PASSWORD`     | Vault login password for `userpass` auth |         | ✔        |
| `HC_VAULT_SECRETS_PATH` | Vault secrets path                       |         | ✔        |
| `ENV_FILE_NAME`         | Name of created env-file                 | .env    |          |
