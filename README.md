# composer_bundle typo3 11.5
 
# DEVELOPER SETUP

## Install composer

though homebrew (macOS)
```shell
brew install composer
```

from the composer website
```shell
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php composer-setup.php
php -r "unlink('composer-setup.php');"
```

## Install ddev

though homebrew (macOS)
```shell
brew install drud/ddev/ddev
```

## Checkout siteroot repository

The repository location on gitlab:

https://gitlab.edelman-stage.de/sitekit-current/siteroot


```shell
mkdir sitekit-current
git clone https://gitlab.edelman-stage.de/sitekit-current/siteroot ./sitekit-current
```

## Initial steps

* copy ```_LocalConfiguration.php``` to ```LocalConfiguration.php```
* copy ```_PackageStates.php``` to ```PackageStates.php```


## Bootstrap project

```shell
ddev start
ddev auth ssh
ddev composer i
```

## Database

get appropriate dump as sql | gz | tgz | ... and import into db inside ddev:

```shell
ddev import-db -f {insert-path-to-dump-file}
```

Now login to backend should work.

## Optional for new projects: import default be_users / be_groups

get appropriate dump as sql | gz | tgz | ... and import into db inside ddev:

```shell
ddev mysql < be_groups_users.sql
```

## Create siteconfig 

Copy siteonfig from edelman-stage.de and change domain name or create siteconfig from scratch in TYPO3.

If necessary get fileadmin assets from stg/live - all should be set.

<p>&nbsp;</p>
<p>&nbsp;</p>

# For Project Maintainers only
[Howto: Setup new website project in gitlab](README-gitlab.md)