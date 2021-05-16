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
rcsync     push     >>>  push hacia el servidor                                                                                                                                                              
rcsync     pull     >>>  pull. del servidor a local                                                                                                                                                           
rcsync     local    >>>  Sincronizar hacia al servidor, siempre que haya cambios                                                                                                                                   
rcsync     server   >>>  Sincronizar del servidor a local                                                                                                                                                          
rcsync     mount    >>>  Montar directorios añadidos en el archivo de configuración   
```

