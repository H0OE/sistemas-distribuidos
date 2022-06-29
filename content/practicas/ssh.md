---
title: 🍣 SSH
banner_icon: 🍣
---

## Prerequisitos
instalar vim
```
apt-get install vim
```

## Cambiar puerto
Ir a:
```
vim /etc/ssh/sshd_config
```

se encontrara una linea asi:
```
#Port 22
```
para cambiar el puerto por el que se conectael ssh, por ejemplo a 234 se descomenta y se cambia el numero, por defecto es 22
```
Port 234
```

## Permitir determinados usuarios
Permitir que solopuedan hacer loggin solo algunos usuarios, agregar al final del documento:
```
AllowUsers Joel
```
Permitir a usuarios de un determinado grupo
```
AllowGroups Marketing
```

## Permitir loggin como root
Buscar la linea
```
#PermitRootLogin prohibit-password
```

y cambiarla a:
```
PermitRootLogin Yes
```

## Importante
Siempre reiniciar el servicio para aplicar cambios
```
/etc/init.d/sshd restart
```