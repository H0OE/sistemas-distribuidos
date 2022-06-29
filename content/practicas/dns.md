---
title:  💫 DNS
banner_icon: 🏜️
---

## Prerequisitos
Tener aptitude
```
apt-get install aptitude
```

## Instalar Bind9
```
aptitude install bind9 bind9-dnsutils bind9utils
```
El archivo por defecto esta en 
```
dpkg -s bind9
```
### DNS
Editar el conf
```
vim named.conf.local
```
copiar el default para nuestra propia zona
```
cp db.0 /var/lib/bind/servidores.com.zone
```
editarlo
```
vim /var/lib/bind/servidores.com.zone
```

Para comprobar se puede usar nslookup y dig