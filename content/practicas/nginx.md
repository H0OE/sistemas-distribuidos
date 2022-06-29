---
title:  💫 Nginx
banner_icon: 💫
---

## Prerequisitos
Tener aptitude
```
apt-get install aptitude
```

## Instalar Nginx
```
aptitude install  nginx
```
El archivo por defecto esta en 
```
/usr/share/nginx/html/index.html
```

### Añadir pagina
Añadir carpeta y su index
```
mkdir /var/www/nuevapag.com
```
dar permisos
```
chmod -R 755 /var/www/
```

Copiar el archivo de configuracion

```
cp /etc/nginx/sites-available/default /etc/nginx/sites-available/nuevapag.com
```

Editar el archivo
```
vim  /etc/nginx/sites-available/nuevapag.com
```

Realizar el link
```
ln -s /etc/nginx/sites-available/nuevapag.com /etc/nginx/sites-enabled/
```

### importante
Agregar en /etc/hosts si se puse nombre de seridor
```
vim /etc/hosts
```
Reiniciar nginx
```
/etc/init.d/nginx restart
```


