---
title: 🏡 Samba
banner_icon: 🏡
---

## Prerequisitos
Tener aptitude
```
apt-get install aptitude
```
Tener un segundo disco
## Instalar samba
```
aptitude install samba
```
```
dpkg -s smbd
```

## Compartir una capeta
Crear una carpeta
```
mkdir compartida
```
Darle permisos
```
chmod 777 -R compartida/
```
Editar el conf, agregar la carpeta compartida
```
vim /etc/samba/smb.conf
```

Reisar bien el path
```
[comartida]

   path = /compartida
   browseable = yes
   read only = yes
   guest ok = no
```

Agregar determinados usuarios
```
[compartida]
	...
	valid users = @marketing
	valid list = @marketing	
```

Agregar usuarios a samba
```
smbpasswd -a pedro
```

### Importante
reiniciar samba
```
/etc/init.d/smd restart
```
## Entrar desde el cliente
Ir al explorador de archivos
```
\\tuip
```
