# PHP7.X - AWSCLI Docker

Docker files with different things for working with Composer, PHPUnit, AWSCLI (Amazon CLI), EB CLI (Amazon Elastic Beanstalk CLI ) to have a better CI/CD but especially to test applications and deploy to Elastic Beanstalk.

Intended for usage in a CI environment (Travis, Gitlab, Drone, etc.):
 - PHP7 CLI (based off the [official](https://hub.docker.com/_/php/) PHP Docker)
 - AWLSCLI (Latest through installer)
 - AWSEBCLI (Latest through installer)
 - Composer (Latest through installer)
 - PHPUnit (7.x )

## Tags And Options

 - `7.2-awscli`: PHP7.2, AWLSCLI, AWSEBCLI, PHPUnit
 - `7.1-awscli`: PHP7.1, AWLSCLI, AWSEBCLI, PHPUnit
 - `7.0-awscli`: PHP7.0, AWLSCLI, AWSEBCLI, PHPUnit
## Usage

## AWS Credentials

To Authenticate with AWS is necessary to set the following ENVIRONMENT VARIABLES:

- **AWS_ACCESS_KEY_ID** – AWS access key.
- **AWS_SECRET_ACCESS_KEY** – AWS secret key. Access and secret key variables override credentials stored in credential and config files.

### Command Line
```
docker pull miguelordonez/php-awscli:7.1-awscli
```

### Gitlab
```
image: miguelordonez/php-awscli:7.1-awscli

before_script:
  - composer install

in_docker:
  stage: test
  script:
    - phpunit
  only:
    - master
```

### Drone
```
build:
  image: miguelordonez/php-awscli:7.1-awscli
  commands:
    - composer install
    - phpunit
```

## Copyright

MIT Licensed. For complete license, see `LICENSE`
