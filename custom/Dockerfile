FROM litespeedtech/openlitespeed:latest

# RUN apt-get update -y && apt-get upgrade -y && apt-get install php-dev autoconf automake -y
# RUN wget https://xdebug.org/files/xdebug-3.1.3.tgz
# RUN tar -xvzf xdebug-3.1.3.tgz
# RUN cd xdebug-3.1.3 \
#     && phpize \
#     && ./configure \
#     && make \
#     &&  cp modules/xdebug.so /usr/local/lsws/lsphp80/lib/php/20200930 \
#     && mkdir -p /usr/local/lsws/lsphp80/etc/php/8.0/mods-available/ \
#     && ls /usr/local/lsws/lsphp80/etc/php/8.0/mods-available/ \
#     && echo 'zend_extension = xdebug' > /usr/local/lsws/lsphp80/etc/php/8.0/mods-available/99-xdebug.ini \
#     && ls /usr/local/lsws/lsphp80/etc/php/8.0/mods-available/
RUN apt update -y && apt upgrade -y && apt install lsphp80-pear -y
RUN mkdir -p /usr/local/lsws/lsphp80/etc/php/8.0/mods-available/ \
    && echo 'zend_extension = xdebug' > /usr/local/lsws/lsphp80/etc/php/8.0/mods-available/99-xdebug.ini
RUN /usr/local/lsws/lsphp80/bin/pecl install xdebug 
RUN echo " \
zend_extension=/usr/local/lsws/lsphp80/lib/php/20200930/xdebug.so\n \
xdebug.var_display_max_children = 999\n \
xdebug.var_display_max_data = 99999\n \
xdebug.var_display_max_depth = 100\n \
xdebug.remote_enable=On\n \
xdebug.remote_host=localhost\n \
xdebug.remote_port=9000\n \ 
xdebug.remote_handler=dbgp" >> /usr/local/lsws/lsphp80/etc/php/8.0/litespeed/php.ini 