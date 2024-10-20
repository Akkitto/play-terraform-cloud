# Play Terraform Cloud

Playing around with Terraform for educational purposes.

## Setup
1. Set up [LocalStack](https://github.com/localstack/localstack) on a VPS.
2. Put the [LocalStack](https://github.com/localstack/localstack) instance behind a reverse proxy with SSL termination and basic authentication.
3. Edit `proxy/docker-compose.yml` by setting `CUSTOM_CRED_BASIC_AUTH` to the Base64-encoded basic authentication token of the reverse proxy in front of [LocalStack](https://github.com/localstack/localstack).
4. Edit `proxy/docker-compose.yml` by setting `CUSTOM_URL_AWS` to the domain, where the [LocalStack](https://github.com/localstack/localstack) instance is hosted on.
5. `cd proxy ; docker-compose up -d`
6. Iterate through exemplary Terraform lifecycle.
    ```
    #!/bin/bash
    file_tfplan="first.tfplan"
    terraform init
    terraform validate
    terraform fmt
    terraform plan "-out=${file_tfplan}"
    terraform apply "${file_tfplan}"
    terraform state list
    terraform destroy
    ```