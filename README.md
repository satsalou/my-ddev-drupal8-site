# my-ddev-drupal8-site

This is a Drupal 8 project with DDEV configuration

## How to install and run
### Install Docker
You need to [install Docker](https://docs.docker.com/engine/install/) as a prerequisite.

### Install DDEV
to install DDEV execute the following command:
```
curl -L https://raw.githubusercontent.com/drud/ddev/master/scripts/install_ddev.sh | bash
```

### Start the container
Run `ddev start`

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
To capture the configuration of the whole website run:
```
ddev exec drush cex
```
