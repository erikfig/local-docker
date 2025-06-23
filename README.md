# Local Docker

This Docker service is used in my local environment to start the most common services used by me.

> This is for my personal use, if i could help i will be happy!
> Sorry for my english, i'm trying very hard

Tested in 

- [x] Fedora Linux
- [x] Windows 11 WSL2
- [x] MacOS

## Services available

 - postgres
 - rabbit
 - nats
 - redis
 - aws (Read next)


## AWS

To configure AWS Service, add an alias to you terminal (`.zshrc` in my case):

```cli
alias aws="docker run --rm -ti -v ~/.aws:/root/.aws -v $(pwd):/aws amazon/aws-cli"
```

Reload your configurations (`source .zshrc` in my terminal or close all terminals and reopen).

Test:

```cli
aws --version
```

And configure:

```
aws configure
```

All informations can be found or generated in AWS Console > Your user (top-right) > Security Credentials.

## LocalStack

- [Install LocalStack CLI](https://docs.localstack.cloud/getting-started/installation/)

If you need to validate your LocalStack configuration in `docker-compose`:

```bash
localstack config validate --file docker-compose.yaml
```

To open the dashboard:

 - [WEB](https://app.localstack.cloud/dashboard)
 - [Desktop](https://app.localstack.cloud/download)

 ## User  Guides

[User Guides](https://docs.localstack.cloud/user-guide/)

## AWS CLI integration

Inside your `~/.aws` directory, create `config` and `credentials` files with with the following content:

config:

```ini
[profile default]
region=us-east-1
output=json
endpoint_url = http://host.docker.internal:4566
```

credentials

```ini
[default]
aws_access_key_id=test
aws_secret_access_key=test
```

- Replace `[default]` and `[profile default]` with `[localstack]` and `[profile localstack]` if you want to keep your AWS account as the default.
- Change `endpoint_url` from `http://host.docker.internal:4566` to `http://localhost:4566` if you’re not using the AWS CLI inside Docker..
