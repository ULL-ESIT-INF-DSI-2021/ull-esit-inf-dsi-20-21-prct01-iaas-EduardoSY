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
![Imagen IaaS](https://github.com/ULL-ESIT-INF-DSI-2021/ull-esit-inf-dsi-20-21-prct01-iaas-EduardoSY/blob/main/docs/img/iaas_UI.png)
Aquí nos tenemos que fijar en la parte que pone **Direccion IP**. Esa será la dirección de nuestra máquina y la que usaremos para conectarnos.
