# New Server Setup

Based on Ubuntu server 11.10

1. `mkdir /root/.ssh`
1. `touch /root/.ssh/authorized_keys`
1. Add relevant public keys to root's `authorized_keys` file.
1. `sudo apt-get update`
1. `apt-get -y install shorewall apache2 monit build-essential git-core mysql-server mysql-client monit php5 php5-mysql php5-gd php5-curl php-pear postfix ruby1.9.1 libyaml-dev`
1. `pecl install yaml`
1. `cd /usr/share/doc/shorewall/default-config`
1. `cp modules* helpers shorewall.conf /etc/shorewall/`
1. `wget https://raw.github.com/SeenHub/server-config/master/etc/shorewall/interfaces`
1. `wget https://raw.github.com/SeenHub/server-config/master/etc/shorewall/policy`
1. `wget https://raw.github.com/SeenHub/server-config/master/etc/shorewall/rules`
1. `wget https://raw.github.com/SeenHub/server-config/master/etc/shorewall/zones`
1. `cd /etc/default`
1. `rm shorewall`
1. `wget https://raw.github.com/SeenHub/server-config/master/etc/default/shorewall`
1. `service shorewall start`
1. `cd /etc/monit/conf.d`
1. `wget https://raw.github.com/SeenHub/server-config/master/etc/monit.d/apache`
1. `wget https://raw.github.com/SeenHub/server-config/master/etc/monit.d/mysql`
1. `service monit restart`
1. `cd /etc/php5/conf.d`
1. `wget https://raw.github.com/SeenHub/server-config/master/etc/php5/conf.d/yaml.ini`
1. `a2enmod rewrite`
1. `a2enmod headers`
1. `a2enmod expires`
1. `a2dissite default`
1. `service apache2 restart`
1. `gem install bundler`
1. `cd /etc/sudoers.d`
1. `wget https://raw.github.com/SeenHub/server-config/master/etc/sudoers.d/deploy`
1. `chmod 0440 deploy`
1. `groupadd -g 1000 deploy`
1. `useradd -m -s /bin/bash -u 1000 -G deploy,staff,www-data deploy`
1. `usermod -a -G deploy www-data`
1. `chgrp -R deploy /var/www /etc/apache2/sites-available/ /etc/apache2/sites-enabled/`
1. `chmod g+w /var/www /etc/apache2/sites-available/ /etc/apache2/sites-enabled/`
1. `su deploy`
1. `ssh-keygen -t rsa`
1. Add relevant public keys to deploy's `authorized_keys`
