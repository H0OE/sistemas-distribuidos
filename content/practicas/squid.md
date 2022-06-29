---
title:  💫 Squid
banner_icon: 💫
---

## Prerequisitos
Tener aptitude
```
apt-get install aptitude
```

## Instalar Squid
```
aptitude install  squid
```
```
dpkg -s squid
```

Editar el conf en la linea 1144
```
vim /etc/squid/squid.conf
```

### importante
Reiniciar squid
```
/etc/init.d/squid restart
```