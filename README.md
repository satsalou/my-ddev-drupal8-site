# my-ddev-drupal8-site

This is a Drupal 8 project with DDEV configuration

## How to install and run
### Install Docker
You need to [install Docker](https://docs.docker.com/engine/install/) as a prerequisite.

### Install DDEV
To install DDEV execute the following command:
```
curl -L https://raw.githubusercontent.com/drud/ddev/master/scripts/install_ddev.sh | bash
```

### Start the container
Run `ddev start`

### Install dependencies
Run `ddev composer install`

### Install website
To install the Drupal website run:
```
ddev exec drush site-install --account-name=admin --account-pass=password
```

### Launch website
To launch the website in the browser run:
```
ddev launch
```

## Launch PHPMyAdmin
To launch PHPMyAdmin run:
```
ddev launch -p
```

## See project info
To see all the project info and configuration run:
```
ddev describe
```

## Capture website configuration
### Export
To export the configuration of the whole website run:
```
ddev exec drush cex
```
### Import
To import the configuration of the whole website run:
```
ddev exec drush cim
```

## Capture website content
### Enable Default Content Deploy and Better Normalizers modules
```
ddev exec drush en default_content_deploy
ddev exec drush en better_normalizers
```
### Set content directory
Set the content directory in the `/web/sites/default/settings.ddev.php`.
```
// Relative path.
$settings['default_content_deploy_content_directory'] = '../config/content-dev';
```
### Export whole site
Create a folder under `/config` and name it "content-dev". Then, run:
```
ddev exec drush dcdes
```
Also, manually move the directories/files of the `web/sites/default/files` folder to `config/files-dev`.
(Select only the necessary files such as images.)

### Import whole site
```
ddev exec drush dcdi --force-update
```
Also, manually copy the assets from `config/files-dev` to `web/sites/default/files/`.
```
cp config/files-dev/* web/sites/default/files/ -r
```
### Clear cache and run cron
Finally, clear caches and run cron
```
ddev exec drush cr
ddev exec drush cron
```
