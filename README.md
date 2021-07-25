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


## Archivos de configuración
- webdav:        añade las variables de la nube, directorio local,... a sincronizar o montar
- webdav.sync  : Directorios o archivos a sincronizar con rclone (solo se sincronizaran los instroducidos en este archivo)


## Sincronización bidireccional
Sincronización bidireccional de la nube webdav

```
rcsync sync webdav
```


## Mis dotfiles
Descargando mis dotfiles del servidor

```
rcsync pull dotfiles
```

Subiendo los cambios de mis dotfiles al servidor

```
rcsync push dotfiles
```


## Inicia al arrancar el sistema
Utiliza cron para iniciar rcsync al iniciar el sistema y hacer una sincronización bidireccional:

```
@reboot ( sleep 30 && rcsync sync wdsm )
```



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

