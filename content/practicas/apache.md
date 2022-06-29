---
title: 🕸️ Apache
banner_icon: 🕸️
---

## Prerequisitos
Tener aptitude
```
apt-get install aptitude
```
Tener un segundo disco
## Instalar apache2
```
aptitude install apache2
```
```
dpkg -s apache2
```
darle permisos a /var/www
```
chmod 755 -R /var/www/
```

Y ya deberia estar corriendo, si se va a nuestra ip en el navegador aparecera la pagina de apache por defecto, la cual esta en /var/www/html/index.html.

## Agregar paginas
crear nuestra carpeta e index para nuestra nueva pagina, editar el index
```
mkdir /var/www/nuevapag
```
```
vim /var/www/nuevapag/index.html
```
Copiar el default conf para la nueva pagina
```
cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/nuevapag.com.conf
```
editar el archivo
```
vim /etc/apache2/sites-available/nuevapag.com.conf
```

donde dice virtual host se puede cambiar el puerto de este por defecto esta 80
```
<VirtualHost *:80>
```

tambien se puede poner un nombre para no solo ingresar por ip
```
ServerName www.nuevapag.com
```
Cambiar el DocumentRoot al creado
```
DocumentRoot /var/www/nuevapag
```
Agregar el sitio
```
a2ensite nuevapag.com.conf
```

Si se agrego un servername agregar a /etc/hosts
```
vim /etc/hosts
```
```
tu-ip www.nuevapag.com
```
ejemplo
```
192.168.34.122 www.nuevapag.com
```
Si se cambio el puerto agregar un listen al puerto correspondienteen /etc/apache2/ports.conf
```
vim /etc/apache2/ports.conf
```
```
Listen 891
```
## Importante
Reiniciar el apache2
```
systemctl restart apache2
```