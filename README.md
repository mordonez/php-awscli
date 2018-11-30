# PHP7.X - AWSCLI Docker

Docker files with different things for working with Composer, AWSCLI (Amazon CLI), EB CLI (Amazon Elastic Beanstalk CLI), PHPUnit to have a better CI/CD but especially to test applications and deploy to Elastic Beanstalk.

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

To Authenticate with AWS is necessary to set the following [ENVIRONMENT VARIABLES](https://docs.aws.amazon.com/cli/latest/userguide/cli-environment.html):

- **AWS_ACCESS_KEY_ID** – AWS access key.
- **AWS_SECRET_ACCESS_KEY** – AWS secret key. Access and secret key variables override credentials stored in credential and config files.
## AWS Elastic Beanstalk

If you want to use the docker image to deploy to Elastic Beanstalk you must have at your application's root the [*.elasticbeanstalk/config.yml*](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/environment-configuration-methods-before.html#configuration-options-before-configyml) file with the info of your Environment.

```
branch-defaults:
  master:
    environment: YOUR-APP-HERE //(Exmaple: MyApp-dev)
global:
  application_name: YOUR-APP-NAME-HERE //(Exmaple: MyApp)
  default_platform: YOUR-APP-NAME-HERE //(Example: PHP 7.1)
  default_region: YOUR-DEFAULT-REGION //(Example: eu-west-1)
  sc: git
  workspace_type: Application
```

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

deploy:
  stage: deploy
  script:
    - eb deploy YOUR-EB-APP-HERE
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
