[![tests](https://github.com/ddev/ddev-mongo/actions/workflows/tests.yml/badge.svg)](https://github.com/RobertLang/ddev-w3c-validator/actions/workflows/tests.yml) ![project is maintained](https://img.shields.io/maintenance/yes/2025.svg)

## What is ddev-wc3-validator?

This repository is an add-on that provides W3c html validation for [DDEV](https://ddev.readthedocs.io/en/stable/).

It's based on [Nu Html Checker on GitHub](https://github.com/validator/validator/pkgs/container/validator) and [DDEV custom compose files](https://ddev.readthedocs.io/en/stable/users/extend/custom-compose-files/) and [DDEV custom commands](https://ddev.readthedocs.io/en/stable/users/extend/custom-commands/).

## Installation

For DDEV v1.23.5 or above run

```bash
ddev add-on get RobertLang/ddev-w3c-validator
```

For earlier versions of DDEV run

```bash
ddev get RobertLang/ddev-w3c-validator
```

Then restart your project

```bash
ddev restart
```
---

## Configuration
### 1. Port used for validator
The PORT for the html-checker web service can be changed in the `.env.validator`:
```dotenv
#ddev-generated
VALIDATOR_PORT=9300
```
Note: If you change the port you should remove `#ddev-generated` to prevent the file from being overwritten during installation.
### 2. Ignoring error for cli validation
Single errors or notices in `ddev validate-cli ...` command can be filtered out by adding them to `.ddev/validator/filter.txt` (one rule per line):

   ```txt
   Trailing slash on void elements has no effect and interacts badly with unquoted attribute values.
   ```
   Error message with the provided text will then be ignored and not reported - [see documentation of The Nu Html Checker (v.Nu)](https://validator.github.io/validator/#:~:text=warnings%20to%20stderr%5D-,%2D%2Dfilterfile%20FILENAME,-Specifies%20a%20filename).

----
## Features

### Command `ddev validate <url>`

This command will open the validator website `https://<projectname>.ddev.site:<VALIDATOR_PORT>/` in your local browser and start checking the provided `<url>` for errors.


### Command `ddev validate-cli <url>`
This command will run the cli version of vnu testing the provided `<url>`. Please [read the documentation](https://www.mongodb.com/docs/mongodb-shell/) for more information.


     Note: If `<url>` is omitted in any of the commands, the default `$DDEV_PRIMARY_URL` of the project will be used.


**Based on the original [ddev-contrib recipe](https://github.com/ddev/ddev-contrib/tree/master/docker-compose-services/mongodb)**

**Maintained by [@RobertLang](https://github.com/RobertLang)**
