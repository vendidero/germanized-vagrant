# Time syncing issues

In case hosts sleeps, VM will possibly be out of snyc. Login via SSH and exec the following:

```shell
sudo service ntp stop && sudo ntpd -gq && sudo service ntp start
```

# Sync MySQL table

To import MySQL data, ssh into vagrant and import data:

```shell
ssh vagrant
cd /srv/www/vendidero
mysql -u root -p vendidero < dump.sql
```

After that use WP CLI to search-replace e.g.:
```shell
wp search-replace 'domain.de' 'domain.wordpress.test' wp_posts
```

# Use ElasticSearch

We are currently using this repo to enable ES support: https://github.com/mmcachran/elasticsearch-vagrant
Now add 

```php
define( 'EP_HOST', 'http://10.0.0.11:9200' );
```
to wp-config.php to enable a connection.

# VVV ( Varying Vagrant Vagrants )

[![Codacy Badge](https://api.codacy.com/project/badge/Grade/206b06167aaf48aab24422cd417e8afa)](https://www.codacy.com/gh/Varying-Vagrant-Vagrants/VVV?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=Varying-Vagrant-Vagrants/VVV&amp;utm_campaign=Badge_Grade)

VVV is a local developer environment, mainly aimed at [WordPress](https://wordpress.org) developers. It uses [Vagrant](https://www.vagrantup.com) and VirtualBox, and can be used to build sites, and contribute to WordPress.

## How To Use

To use it, download and install [Vagrant](https://www.vagrantup.com) and [VirtualBox](https://www.virtualbox.org/). Then, clone this repository and run:

```shell
vagrant plugin install vagrant-hostsupdater --local
vagrant up --provision
```

When it's done, visit [http://vvv.test](http://vvv.test).

The online documentation contains more detailed [installation instructions](https://varyingvagrantvagrants.org/docs/en-US/installation/).

* **Web**: [https://varyingvagrantvagrants.org/](https://varyingvagrantvagrants.org/)
* **Contributing**: Contributions are more than welcome. Please see our current [contributing guidelines](https://varyingvagrantvagrants.org/docs/en-US/contributing/). Thanks!

## Minimum System requirements

* [Vagrant](https://www.vagrantup.com) 2.2.6 or below.
* [Virtualbox](https://www.virtualbox.org) 6.0.x or below.
* 8GB+ of RAM
* Virtualisation ( VT-X ) enabled in the BIOS ( Windows/Linux )
* Hyper-V turned off ( Windows )

## Software included

For a comprehensive list, please see the [list of installed packages](https://varyingvagrantvagrants.org/docs/en-US/installed-packages/).
