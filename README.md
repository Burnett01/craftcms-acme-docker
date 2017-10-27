# CraftCMS Acme Docker

This is a boilerplate for Craft CMS and Docker.

## Services

- CraftCMS
- Database (MySQL)
- Mailhog

## Install

--> Edit Hosts:

Make sure to add ``craft.dev`` to your hosts file

--> Clone/Pull this repository:

```
git clone https://gitlab.com/Burnett01/craftcms-acme
```

--> Configure DB:

Edit ``docker-compose.yml`` to configure your database service.

```yaml
MYSQL_USER: acme
MYSQL_PASSWORD: acme
MYSQL_DATABASE: acmedb
```

**Note regarding compose/craft.conf:** The DocumentRoot directive must not be changed. The underlaying docker image of the CraftCMS service requires that path to be present. Soon, you might be able to change it.

## Run
```
docker-compose up
```

**Note** Do not use ``up -d`` if you are running the composition for the first time. Otherwise you won't know whether the download has finished.

The first time you run the composition, CraftCMS will be downloaded to the ``public`` folder and the MySQL service will create a database for you.

That database can be used when installing Craft CMS.

Also make sure to use the credentials of the database service in your ``craft/app/config/db.php`` file.

```php
<?php

return array(

	'server' => 'localhost', // or container IP

	// The name of the database to select.
	'database' => 'acmedb',

	// The database username to connect with.
	'user' => 'acme',

	// The database password to connect with.
	'password' => 'acme',

	// The prefix to use when naming tables. This can be no more than 5 characters.
	'tablePrefix' => 'craft',

);
```

## Hit it up / Install Craft CMS

http://craft.dev/admin/install

