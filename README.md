# rcsync

Sincronización de directorios con multitud de nubes públicas o privadas.

- Sincronización automatizada con inotify, tanto en linux como android.
- **En Android es necesario crear previamente el directorio que vamos a sincronizar**


## Instalación
```
sudo curl -L https://raw.githubusercontent.com/uGeek/rcsync/master/rcsync \                                                                         ✔  
          -o /usr/bin/rcsync && sudo chmod +x /usr/bin/rcsync
```


## Instalación en Ubuntu

```
bash <(curl https://raw.githubusercontent.com/uGeek/rcsync/main/rcsync) install ubuntu
```

## Instalación en Termux (Android)


```
bash <(curl https://raw.githubusercontent.com/uGeek/rcsync/main/rcsync) install termux
```

### Sincronizando




## Instalación en el sistema

Si tu distro no ejecuta los scripts en el directorio `$HOME/.local/bin/` puedes crear una enlace simbólico

```
sudo chmod +x /home/$USER/.local/bin/rcsync
sudo ln -s /home/$USER/.local/bin/rcsync /usr/bin/rcsync
```

## Paquetes necesarios
### Instala **RCLONE** y **curl**.


#### RCLONE
```
curl https://rclone.org/install.sh | sudo bash
```
#### curl

```
sudo apt install curl
```


### Para notificaciones inotify-tools

```
sudo apt install inotify-tools
sudo apt install notify-osd     ## ubuntu
sudo apt install libnotify-bin  ## debian    
```

### Para utilizar los archivos cifrados de rclone, dialog

```
sudo apt install dialog
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


## Termux
Instalar y configurar en Termux para Android.

Sincronización mediante el Widget de Termux

[Wiki Termux](https://wiki.termux.com/wiki/Main_Page)


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
rcsync   mount   nube c >>>  Archivo de configuración de rclone cifrado

rcsync   mount   nube   >>>  Montar directorios añadidos en el archivo de configuración

  Ejemplo: Mi nube se llama webdav
    - Sincronizar a la nube todo lo que hago en mi escritorio: rcsync local webdav
    - Sincronización Bidireccional:                            rcsync sync  webdav 
    - Montar directorios configurados en el archivo config:    rcsync mount webdav

  Ejemplo: Mis dotfiles estan en la nube dot
    - Subir al servidor los cambios de dotfiles en mi PC:      rcsync push dot
    - Descargar los dotfiles de mi servidor al PC:             rcsync pull dot 
```

