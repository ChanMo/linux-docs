Apache
=======

安装
------

Archlinux::

  sudo pacman -S apache2

Ubuntu::

  sudo apt-get install apache2


使用HTTPS
----------

修改站点配置文件::

  vim site.conf

  <VirtualHost *:443>
    SSLEngine on
    SSLCertificateFile /path/to/crt
    SSLCertificateKeyFile /path/to/key
    ServerName site.com
    ...
  </VirtualHost>

