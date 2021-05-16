# rcsync


## Instalación

Instala **rcsync** en tu dispositivo con linux

```
git clone https://github.com/uGeek/rcsync.git ~/rcsync
```

```
sudo ln -s /home/angel/rcsync/rcsync /usr/bin/rcsync
sudo chmod +x /usr/bin/rcsync
```

### Instala **RCLONE** y **curl**.


#### RCLONE
```
curl https://rclone.org/install.sh | sudo bash
```
#### curl

```
sudo apt install curl
```


### Necesita los siguientes paquetes:

```
sudo apt install inotify-tools
sudo apt install notify-osd     ## ubuntu
sudo apt install libnotify-bin  ## debian    

```


## Iniciar sincronización o montaje de nubes

Cada vez que inicies por primera vez una nubes, o quieras cambiar de nubes,indica con este comando la fuente del archivo configuración:
Ejemplo:

```
echo "source ~/.config/rcsync/webdav" >  ~/.config/rcsync/source  
```



## Archivos de configuración
- webdav:        añade las variables de las nubes, directorio local,... a sincronizar
- webdav.sync  : Directorios o archivos a sincronizar con rclone


## Opciones

```
---------------------------------------------------------------------------------
rcsync     [opción]      Descripción
---------------------------------------------------------------------------------
rcsync   push    nube   >>>  push hacia el servidor
rcsync   pull    nube   >>>  pull. del servidor a local
rcsync   local   nube   >>>  Sincronizar hacia al servidor, siempre que haya cambios
rcsync   server  nube   >>>  Sincronizar del servidor a local
rcsync   sync    nube   >>>  Sincronización con la nube bidireccional
rcsync   config         >>>  Ver confiruración de última nube utilizada

rcsync   mount   nube   >>>  Montar directorios añadidos en el archivo de configuración

  Ejemplo: Mi nube se llama webdav
    - Sincronizar a la nube todo lo que hago en mi escritorio: rcsync local webdav
    - Sincronización Bidireccional:                            rcsync sync  webdav 
    - Montar directorios configurados en el archivo config:    rcsync mount webdav

  Ejemplo: Mis dotfiles estan en la nube dot
    - Subir al servidor los cambios de dotfiles en mi PC:      rcsync push dot
    - Descargar los dotfiles de mi servidor al PC:             rcsync pull dot 
```

