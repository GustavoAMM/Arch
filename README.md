# Instalar Arch "fácil"

## Particiones

Tener dos particiones ya hechas:

- 500 MB -> Para la partición de /boot
- 50 GB -> Para el Sistema operativo

Las particiones se pueden hacer desde la **administración de discos** en Windows.

![Windows](Win.jpg)

## USB booteable

- Descargar la iso de [Arch](https://archlinux.org/download/).
- Descargar [Rufus](https://rufus.ie/es/).

Lo siguiente es quemar la iso en una USB minimo de 8G.

- Abrir Rufus
- Seleccionar la iso y la USB.
- Dar click en EMPEZAR

![Rufus](Rufus.jpg)

## Iniciar USB 

- Reiniciar la computadora con la USB conectada.
- Antes de encender completamente, abrir el Windows Boot Manager. (Presionar F12)
- Seleccionar la USB.

![Boot](Boot.png)

- Inicar la iso de archlinux

![Iso](Iso.jpg)

- Esperar a la carga completa de la iso

![Root](Root.png)
## Teclas

Para cambiar la configuración del teclado a español.

```
loadkeys es
```
## Tarjeta de red

Por defecto no tendremos conexión a internet y para comprobar podemos usar el siguiente comando para verificar que no tendremos respuesta.

```
ping 8.8.8.8
```

![PingNO](PingNo.png)

Muchas computadoras portátiles tienen un botón (o interruptor) de hardware para apagar la tarjeta inalámbrica; sin embargo, el kernel también puede bloquear la tarjeta. 

Para ver el estatus de nuestros dispositivos inalámbricos podemos usar el siguiente comando:

```
rfkill
```
 ![Red](RedBlo.png)

Podemos ver que nuestra tarjeta wifi esta bloqueada y para desbloquear usamos el siguiente comando:

```
rfkill unblock wifi
```

y podemos volver a a verificar el estatus de nuestros dispositivos inalámbricos para comprobar que estan desbloqueados.

![Red](RedU.png)

## Red

Para conectarnos a una red wifi vamos a utilizar una herramienta llamada **iwctl**

Debemos conocer dos cosas para conectarnos a internet:

- EL SSID (Nombre de nuestra de red)
- El password de la red

Para conectarnos usamos el siguiente comando:

```
iwctl --passphrase CONTRASEÑA_RED station wlan0 connect NOMBRE_RED
```

> En dado caso que nuestro nombre de red tenga caracteres especiales como por ejemplo: guiones, signos, etc.
>
> El nombre debe de ir entre comillas: "NOMBRE_RED"
>
> En dado caso que nuestra red no tenga contraseña puedes poner "" donde va la contraseña

Para verificar que ya contamos con internet mandamos un ping y esta vez tendremos respuesta.

```
ping 8.8.8.8
```
![Ping](Ping.png)

## Instalación 

Para instalar fácilmente Arch Linux podemos usar el instalador que tiene incluida la iso.

Usamos el siguiente comando:

```
archinstall
```

Se descarga e inicializa el instalador.

![Archinstalll](Arch_img/Archinstall.png)

## Proceso de instalación

Se va a ir dando enter en cada opción y se irá personalizando según los siguientes pasos:

- Idioma de Archinstall

> Poner el idioma del instalador en español

![idioma](Arch_img/Lenguage.png)

- Distribución del teclado

> Seleccionar la distribución de tu teclado, en este caso latinoaméricano

![Teclado](Arch_img/Teclado.png)

- Región del servidor

> Seleccionar el servidor donde se van a descargar los paquetes

![Servidor](Arch_img/Paquetes.png)

- Idioma local

> Seleccionar el idioma local para tu sistema operativo

![Idioma](Arch_img/Idioma.png)

- Codificación local

> Seleccionar codificación local de los caracteres

![Codificación_local](Arch_img/Codificacion.png)

- Discos

> Seleccionar tu disco principal donde se va a instalar el SO

![Discos](Arch_img/Disco.png)

- Diseño del disco

> Seleccionar la partición manual (seleccionar que hacer con cada unidad individual)

![Diseño](Arch_img/unidad.png)

## Particiones individuales

> Tener CUIDADO con los siguientes pasos, puedes borrar windows

Identificar tus dos particiones:

- la partición de 500MB
- la partición de 50G

Formatear las dos particiones para que el apartado de wipe cambie a true

La primera partición (500MB) es la boot donde esta el kernel del sistema operativo con archivos para el arranque.

- Sistema de archivos

![Fat32](Arch_img/fat32.png)

La segunda partición (50G) es la raiz donde esta el sistema operativo

![ext4](Arch_img/ext4.png)

La tabla de particiones queda asi:

![Tabla](Arch_img/tabla.png)

- Puntos de montaje

Ahora vamos a montar las particiones que acabamos de hacer.

![Montaje](Arch_img/0.png)

Vamos a seleccionar cada una y montar de manera individual

La primera de boot vamos a montar en /boot

![Boot](Arch_img/boot.png)

La seguna de raiz vamos a montar en /

![Raiz](Arch_img/raiz.png)

La tabla final de las particiones queda asi, mas las particiones de windows.

![FInal](Arch_img/TablaFinal.png)
