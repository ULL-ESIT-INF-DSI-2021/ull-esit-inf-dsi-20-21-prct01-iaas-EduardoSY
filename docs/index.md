# Práctica 1 - Configuración de máquina virtual en el IaaS
* Universidad de La Laguna
* Eduardo Da Silva Yanes 

## 1. Introduccion
En esta primera práctica de la asignatura de Desarrollo de Sistemas Informáticos debemos configurar nuestra máquina virtual alojada en el IaaS con la que haremos las prácticas. Configuraremos tanto en entorno de la máquina, instalando y configurando git y Node.js y la conexión ssh.
### Objetivos
1. Configurar nuestra máquina virtual del IaaS
2. Configurar nuestra conexión SSH con la máquina del IaaS
3. Instalar y configurar la conexión con Github
4. Instalar Node.js 

## 2. Requisitos previos
Para poder realizar esta primera práctica (y todas las que continuan) necesitamos conectarnos a la web del [IaaS](iaas.ull.es). Para ello es necesario utilizar una VPN para poder acceder. Si al acceder al sitio web nos sale un error de "No se puede acceder al sitio" o similar, probablemente no estemos conectados a la VPN. Si no sabemos como hacerlo podemos seguir la guía para [Configurar VPN ULL](https://www.ull.es/servicios/stic/2020/12/01/servicio-de-vpn-de-la-ull/).
También será necesario tener una cuenta de Github ya que será donde volcaremos las tareas que hagamos en un futuro.

## 3. Desarrollo de la práctica

### 3.1 Conectandose por primera vez al IaaS
Lo primero que haremos será conectarnos a la página web del [IaaS](iaas.ull.es). Recordemos que es necesario tener configurada la VPN para establecer conexión tanto con la web como con nuestra máquina. En caso de no haberlo hecho revise el apartado de **Requisitos previos**.
Una vez entramos en la página, introducimos nuestras credenciales institucionales y se nos mostrará una intefaz con las máquinas que hemos creado o tenemos disponibles. Seleccionamos la que pone **DSI** y le damos a ejecutar. Cuando esté lista se nos agregará una máquina con un número de sufijo.
Accedemos a ella y veremos una pantalla como la que se muestra a continuación.
![Imagen IaaS](img/iaas_UI)
Aquí nos tenemos que fijar en la parte que pone **Direccion IP**. Esa será la dirección de nuestra máquina y la que usaremos para conectarnos.
Abrimos una terminal y nos conectamos por SSH. Introducimos la dirección que tenga nuestra máquina.
En mi caso es:
```bash
ssh usuario@10.6.131.65
```
*** IMAGEN ***
Es la primera vez que nos conectamos asi que nos aparecerá un mensaje al que debemos responder afirmativamente. Las credenciales están por defecto asi que nuestra contraseña es "usuario". 
Una vez hemos establecido conexión el sistema nos obliga a establecer una contraseña nueva. Ponemos la que queramos. (Primero se nos pide poner la contraseña actual (por defecto) y luego la nueva que queremos poner dos veces.)

*** IMAGEN ***

Lo siguiente que hacemos es personalizar un poco el nombre de la máquina. En lugar de que nos salga "Ubuntu" en el prompt, vamos a hacer que se muestre el nombre de nuestra máquina. En mi caso pondré **iaas-dsi44** ya que mi máquina es la numero 44.
Para hacer este cambio modificamos el fichero _**/etc/hostname**_ y sustituimos el nombre "Ubuntu" por "iaas-dsi44"
```bash
sudo vim /etc/hostname
```
También vamos a cambiar el nombre de host de "Ubuntu" por iaas-dsi44. Para ello modificamos el fichero _**/etc/hosts**_. Simplemente sustituimos el nombre de "Ubuntu" por el de iaas-dsi44.

Como podemos observar parece que no ha habido ningún cambio. Para que las modificaciones que hemos hecho tengan efecto debemos reiniciar el sistema. Pero antes de eso vamos a aprovechar a actualizar y poner todo al día.

```bash
sudo apt update
sudo apt upgrade
```
Una vez finalizados podemos reiniciar
```bash
sudo reboot
```


Ahora vamos a dejar de lado momentaneamente la VM del IaaS para trabajar en nuestro PC local. Algo muy cómodo sería usar el comando SSH y que se conectara automáticamente sin necesidad de tener que poner la contraseña. Eso es precisamente lo que haremos.
Lo primero es revisar si en algún momento ya hemos generado una clave.
```bash
cat .ssh/id_rsa.pub 
```
Si tenemos un output que empieza por **ssh-rsa** significa que en algún momento ya generamos esa clave y no es necesario hacer otra. Si por el contrario obtenemos un error, debemos generar una clave ssh.
Para generar la clave ejecutamos el siguiente comando: 
```bash
ssh-keygen
```
Es importante que usemos los **parametros por defecto** asi que simplemente daremos **enter / intro** hasta que finalice.
Ahora solo falta pasar esta clave desde nuestra máquina local a la máquina de IaaS. Para ello usamos:
```bash
ssh-copy-id usuario@10.6.131.65
```
Ya tenemos nuestro "token de autentificación" en la máquina virtual y podemos iniciar una conexión SSH sin necesidad de poner la contraseña.

### 3.2 Instalación Git

Antes de comenzar con Git vamos a generar una clave pública-privada en nuestra VM del IaaS. Lo haremos siguiendo los pasos anteriores pero sin pasar la clavea ninguna máquina más. Una vez generamos la key no hacemos nada más.

Vamos a comprobar que tenemos **git** instalado. En teoría está instalado por defecto en las máquinas de IaaS. Podemos verificarlo escribiendo "git" en la consola y observando cómo se nos despliega una ayuda o utiizando el comando:
```bash
sudo apt install git
```
Aquí nos va a decir si está instalado o no y si tenemos la versión más reciente. En nuestro caso todo está correcto.
