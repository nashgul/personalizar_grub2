# Como personalizar GRUB2
Guía y archivos para personalizar grub2

## Comprobar que soportamos al menos 1024x768x16

Sería necesario que nuestra bios soporte al menos esa resolución.

Para comprobarlo al iniciar GRUB pulsamos __'c'__, entramos en modo comando y escribimos:

~~~
vbeinfo
~~~

Miramos las resoluciones soportadas.
(Por ejemplo en mi caso la buena es: 1400x1050x32)

## Instalar paquete de tema

Metemos la carpeta del tema en: __/boot/grub/themes__

## Configurar GRUB2 

Editamos las siguientes líneas en __/etc/default/grub__:

~~~
# Esta línea define la resolución del GRUB2.
# La primera deficinión es la que intentará utilizar.
# La segunda deficinión se usará en modo fallback.
GRUB_GFXMODE=1400x1050x32,auto

# Esta línea le dice al grub que intente iniciar el kernel linux con 
# la misma resolución y colores que él.
GRUB_GFXPAYLOAD_LINUX=keep

# Esta línea define que tema se va a cargar
GRUB_THEME="/boot/grub/themes/tema_personalizado/theme.txt"
~~~

Guardamos y ejecutamos el siguiente comando para que los cambios surtan efecto:
~~~
# grub-mkconfig -o /boot/grub/grub.cfg 
~~~

## Reiniciar

Si todo ha ido bien al iniciar debes tener el nuevo tema cargado.









