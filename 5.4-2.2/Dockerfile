FROM openorchestra/open-orchestra:apache2.2

MAINTAINER Raphaël Carles <raphael.carles@businessdecision.com>

RUN systemMods=" \
        php5 \
        libapache2-mod-php5 \
        php5-cli \
        php5-dev \
        php5-mongo \
        php5-curl \
        php5-redis \
        php5-xdebug \
        php5-imagick \
        php5-intl \
        php5-mysql \
        php5-gd \
        php5-ldap \
        php-pear \
        php-apc \
    " \
    && apt-get update && apt-get install -y $systemMods

RUN a2enmod php5

# Install php tools
RUN cd $HOME && \
    wget http://getcomposer.org/composer.phar && \
    chmod +x composer.phar && \
    mv composer.phar /usr/local/bin/composer && \
    wget https://phar.phpunit.de/phpunit.phar && \
    chmod +x phpunit.phar && \
    mv phpunit.phar /usr/local/bin/phpunit && \
	wget https://phar.phpunit.de/phploc.phar && \
    chmod +x phploc.phar && \
    mv phploc.phar /usr/local/bin/phploc && \
    wget http://static.pdepend.org/php/latest/pdepend.phar && \
	chmod +x pdepend.phar && \
	mv pdepend.phar /usr/local/bin/pdepend && \
    wget http://static.phpmd.org/php/latest/phpmd.phar && \
	chmod +x phpmd.phar && \
	mv phpmd.phar /usr/local/bin/phpmd && \
    wget https://squizlabs.github.io/PHP_CodeSniffer/phpcs.phar && \
	chmod +x phpcs.phar && \
	mv phpcs.phar /usr/local/bin/phpcs && \
    wget https://squizlabs.github.io/PHP_CodeSniffer/phpcbf.phar && \
	chmod +x phpcbf.phar && \
	mv phpcbf.phar /usr/local/bin/phpcbf && \
    wget https://phar.phpunit.de/phpcpd.phar && \
	chmod +x phpcpd.phar && \
	mv phpcpd.phar /usr/local/bin/phpcpd && \
    wget https://phar.phpunit.de/phpdcd.phar && \
	chmod +x phpdcd.phar && \
	mv phpdcd.phar /usr/local/bin/phpdcd && \
	wget https://github.com/Halleck45/PhpMetrics/raw/master/build/phpmetrics.phar && \
	chmod +x phpmetrics.phar && \
	mv phpmetrics.phar /usr/local/bin/phpmetrics && \
	wget http://get.sensiolabs.org/php-cs-fixer.phar && \
	chmod +x php-cs-fixer.phar && \
	mv php-cs-fixer.phar /usr/local/bin/php-cs-fixer

COPY ./php/conf.d /etc/php5/apache2/conf.d

RUN echo "xdebug.max_nesting_level = 1000" >> /etc/php5/conf.d/20-xdebug.ini

CMD ["/run.sh"]
