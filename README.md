# Proyecto-Tolerante-a-Fallas 
![image (1)](https://user-images.githubusercontent.com/91103822/205793693-a41a1781-b051-4845-b56a-1a35a220d4d0.png) 
### Servidor de Minecraft 🧊 🐳 ⚓
* Integrantes
  * Juan José Salazar Villegas  ❤❤❤❤❤  🍗🍗🍗🍗
  * Paola Vanessa Del Río Gómez  ❤❤❤❤❤  🍗🍗🍗🍗
  * Juan Emmanuel Fernández de Lara Hernández ❤❤❤❤❤  🍗🍗🍗🍗

***

<!--  IMAGENES DE DOCKER UTILIZADAS-->

#### Imagenes usadas de docker Hub
> Para la practica se utilizo la versión de "Java Edition" (Se anexan las demas versiones por Segun se necesite).
* Doker Images para minecraft:
 * ☕ [itzg/minecraft-server - JAVA](/[es](https://hub.docker.com/r/itzg/minecraft-server)).
 * 🌑 [itzg/minecraft-bedrock-server - BEDROCK](/[es] (https://hub.docker.com/r/itzg/minecraft-bedrock-server)).
 * 🧊 [itzg/bungeecord - CONTENEDOR](/[es] (https://hub.docker.com/r/itzg/bungeecord)).


<!--  CONTEXTO DE PROYECTO-->
### Fundamentos de Desarrollo - Estructura de Servidores

> 📌 Dentro de este Proyecto se busca establecer un servidor de Minecraft el cual con ayuda de 🐳 Docker compose unifique diferentes pots siendo cada uno de estos un mundo distinto el cual con la linea de comandos misma de minecraft nos ayude a desplazar entre estos pots(Mundos) Unificando el trafico por pot y no afectando los demás.
> 
<!--  INSTALAICION DE MINIKUBES-->

# 📥 Instalación de minikube 📥
> ❗ Minikubes nos ayudará como herramienta ya que este virtualizara una maquina la cual nos dara un entorno mas sencillo para trabajar kubernetes
  Para ello usamos los siguientes comandos:
> 
#### Instalación:
    New-Item -Path 'c:\' -Name 'minikube' -ItemType Directory -Force Invoke-WebRequest -OutFile 'c:\minikube\minikube.exe' -Uri   'https://github.com/kubernetes/minikube/releases/latest/download/minikube-windows-amd64.exe' -UseBasicParsing
  
o tambien:
    
    winget install minikube
![image](https://user-images.githubusercontent.com/88942550/204116926-cd6494c2-d3ac-4fe9-a7c1-778d61c3c76d.png)

#### Iniciar Maquina Virtual (Cluster):
    minikube start
    
![image](https://user-images.githubusercontent.com/91103822/205827285-9724a1e3-5f1a-4ba7-9774-ac2f815c092e.png)

# ✔ Activar Hyper-V ✔
> Al trabajar en un entorno de Windows fue necesario el establecer dicha configuracion para la virtualización ademas de que sin ella no tendriamos funcionando nuestro minikubes virtualizado. **Nota:** Si no se virtualiza puede ser necesario buscar en la bios dicho apartado de Intel para su virtualización.
> 

    Get-WindowsOptionalFeature -FeatureName Microsoft-Hyper-V-All -Online
    
![image](https://user-images.githubusercontent.com/91103822/205827719-40623e2f-335a-47fe-8421-c36ed358384b.png)    

### Establecer imagen de HYPER-V
    DISM /online /enable-feature /All/FeatureName:Microsofth-Hyper-V
![image](https://user-images.githubusercontent.com/91103822/205828096-0c94bd88-e801-4319-b2d7-edba6b45cb15.png)

<!--  EXPLICACION MINIKUBE Y KUBERNETES -->

# 🧊 Entorno de Desarrollo kubernetes - minikube 🧊

> Al tener listo nuestra virtualización podremos trabajar facilmente con kubernetes y por ello aplicaremos dischos comandos para ver su funcionamiento y lo que contiene desde nuestro Nodo hasta nuestro pot (Servidor de minecraf). Para inicializar nuestro Cluster de minikube solo basta con contar una manera de Virtualización (Vitual-Box, HyperVizor, Docker Desktop).
> 
### Inicializamos y comprobamos nuestro Cluster
![image](https://user-images.githubusercontent.com/91103822/205562986-34a12e9b-2386-4dab-b764-6aef5ced26e1.png)

#### Los comandos implementados son los siguientes:

**Inicializa Cluster**

    minikube start
 **Confirmamos Funcionamiento de Kubernetes con su versión **   
 
    kubectl version
**Consultamos información de nuestro Cluster**
    
    kubectl cluster-info dump

**Obtenemos los nodos activos**
    
    kubectl get nodes
    
**Creamos nuestra imagen desde Docker Hub**
    
    kubectl create deployment servidor-minecraft --image=itzg/minecraft-server

**Consultamos nuestro deploymen (Pot) de nuestra imagen creada**

    kubectl get deployments

### **🧭Conexion entre host (the online terminal) y el kubernetes cluster:**
![image](https://user-images.githubusercontent.com/91103822/205563141-e32c679c-068d-4953-a9b6-f54301e0024c.png)

**Comando:**

    kubectl proxy
  
### Navegación entre directorios:
**Origen - localhost**
![image](https://user-images.githubusercontent.com/91103822/205563170-fa9f2d27-3db2-45ab-b11f-4b910e6d9b90.png)
**Version **
![image](https://user-images.githubusercontent.com/91103822/205563183-cec21b0e-a1d0-48aa-9d51-0fb40d32994e.png)

> Gracias a este comando podremos saber el nombre de Nuestro pot para operar con el cabe resaltar que cada una de estas al desglosarnos la información podremos is desplazandonos esto en la misma url en este caso usando: 
* Vistas
  * http://127.0.0.1:8001 - Puerto por defecto
  * **/version** - Nos mostrara datos de version de cada dependencia
  * **/pots** - Usado para ver nuestros pods activos y sus caracteristicas viendo su estatus asi como su configuración.
> 
### Directorio de nuestro servidor

![image](https://user-images.githubusercontent.com/91103822/205844441-fb2a3231-5191-4f3f-ae1f-e73cb37f1c19.png)

## Obteniendo nombre de nuestro Pot:

    servidor-minecraft-9c75f8f98-2zz26
    
![image](https://user-images.githubusercontent.com/91103822/205563191-48114723-4d68-4c65-8496-e9502b4a5fc5.png)

***

# 🐳 Creando nuestra imagen en Docker 🐳

> Ahora toca establecer nuestra imagen esto realizandolo con Docker desktop que al igual podemos utilizar la CLI esto usando la imagen anteriormente dicha, Ahora bien este comando no solo creara nuestro contenedor si no que tambien lo nicializara **Ya que con este comando aceptamos la EULA  DE MINECRAFT** haciendo que nos deje descargar las caracteristicas y configuracion base de nuestro servidor que luego podremos editar asi pues este comando hara lo siguiente:
> 

* Partes del comando:
  * **-e EULA=TRUE** - Acepta los terminos y condiciones con Mojang
  * **-p 25565:25565** - Esatableceremos los puertos de acceso.
  * **temp_data2:/data** - Crea los archivos en la carpeta seleccionada "temp_data2" para establecer los datos de nuestro servidor
  * **itzg/minecraft-server:latest** - Establcemos la imagen de Docker Hub asi como la ultima version en la que esta se encuentra disponible.

### Comando de creacion de nuestro Contenedor:
       
    docker run -e EULA=TRUE -p 25565:25565 -v C:\Users\Salvi\Desktop\Minecraft-Docker\temp_data2:/data itzg/minecraft-server:latest



#### **🐳 Contenedor en Doker:**

![image](https://user-images.githubusercontent.com/91103822/204116265-3ca4b3d9-8dde-4fb7-9aab-060a649a5bc6.png)
**Volumen:**<br><br>
![image](https://user-images.githubusercontent.com/91103822/204116282-8ebdce5a-3e8c-4290-9aaa-965294bee084.png)
**Creacion de Mundo:**<br><br>
![image](https://user-images.githubusercontent.com/91103822/204116295-d3e4a245-d4cb-4903-9afb-2d1bd929b62d.png)

**Contenido de servidor:**<br><br>
> Aqui optenemos base a nuestro comando aquellos archivos descargados para que sean configurables en este caso cambiamos el online mode a false permitiendo entrar sin contar con alguna cuenta premium ademas de que podremos cargar nuestros mundos personalizados asi como configurar los puertos , la IP entre otros.
>  
![image](https://user-images.githubusercontent.com/91103822/204116316-f42e18c3-9ce4-4482-b645-639e89197624.png)

***

# 🏔 Configurando Nuestro Servidor en minecraft 🏔

> Estamos a un paso de entrar y disfrutar de nuestro servidor, para ello solo basta con configurar base a los puertos asignados y la ip local nuestro mundo. Para ello noso basta con entrar **Multiplayer - Agregar Servidor - Ponemos el IP (Cambiar el nombre de servidor es opcional)**

**Configuración de Servidor en Minecraft:**<br><br>
![image](https://user-images.githubusercontent.com/91103822/204116533-b70af9d1-8d5d-4e48-b406-a20e5371e28e.png)
### Asiganmos nuestra ip local siendo si es necesario agregar los puertos establecidos:

**IP**
   
    127.0.0.1
 
![image](https://user-images.githubusercontent.com/91103822/204116565-0be16f0d-9e98-42f8-939b-f6fff7721a9b.png)

> Ya configurado podremos acceder a nuestro servidor y jugar normalmente.


***

# ⚙🔧 Apartado de Pruebas ⛏⚙

> Como podremos observar al seguir los pasos e instalar nuestra imagen de minecraft de **Docker hub** podremos entrar facilmente con solo iniciar nuestro cluster o si lo creamos desde 0 con el comando que inicializa nuestro contenedor.
> 

![2022-11-26_20 32 40](https://user-images.githubusercontent.com/91103822/204116729-f06291ff-751b-4670-938d-d62650ab15df.png)
![2022-11-26_20 36 20](https://user-images.githubusercontent.com/91103822/204116730-535bcd2d-b5ed-4929-84a8-9da835017739.png)
![2022-11-26_20 01 00](https://user-images.githubusercontent.com/91103822/204116732-99e8e7ab-1fe6-44db-b069-abcf8bf4238c.png)
![image](https://user-images.githubusercontent.com/91103822/204116673-b20b7a4a-c5ab-4811-8e50-294baa725925.png)

***

# 🗺 Conexion entre mundos (Pots) 🗺

![image](https://user-images.githubusercontent.com/91103822/205848652-1165621e-178c-4e05-b083-fdf92f24e8b2.png)

>Al nosotros tener nuestro primer pot establecido creamos otro mas para tener una conexion entre ellos, ya conectados podemos acceder gracias a docker compose al tener interaccion directa entre aplicaciones o multiples contenedores y estos van de la mano con un archivo **YML** el cual como veremos en nuestros archivos ** Configura los servicios de nuestra aplicacion y posteriormente con un solo comando iniciaremos todos los servicios desde dicha configuración **
>

## POT 1 - Servidor 1 funcional 
![image](https://user-images.githubusercontent.com/91103822/205846174-a83b0137-86de-47af-815e-ab4c068851f6.png)

## POT  - Servidor 2 funcional 
![image](https://user-images.githubusercontent.com/91103822/205846199-e95291c5-e9cf-4cb3-b9fd-5c20ce831f1c.png)

>**NOTA:** Dentro de nuestro archivo YML como observamos tendremos varias instancias las cuales corresponden anuestros mundos asi tendremos el mundo por defecto que entramos (Pot 1) y nuestro segundo mundo denomindao Lobby. Adema de ver como establecemos nuestro servidor podremos ver como cada contenedor es llamado asi como su configuracion al "Spawnear" el usuario.
>

### Declaración de Mundo base (POT 1) 🌎
![image](https://user-images.githubusercontent.com/91103822/205846772-13b41544-8638-4d8e-a66b-28e06e6462b4.png)

### Declaración de mundo Lobby (POT 2) 🌍 
![image](https://user-images.githubusercontent.com/91103822/205847050-9841be78-f865-4b95-8451-8a1527cb68fe.png)

Comandos para cambiar entre mundos:
> Para usar los comandos dentro del juego simplemente abriremos nuestro chat y pondremos siempre " / " al tratarse de un comando siendo de la siguiente manera:
> 

#### Cambiar a Lobby

**De Server (Spawn) a lobby**
   
    / server Lobby
    
**De Lobby a Spawn**
   
    / server server

# 🚫⛔ Chaos Engineering 🚫⛔

> En este apartado se dio pruebas con herramientas de Chaos Engineering esto para ver el tiempo de reacción y restablecimiento de nuestra aplicacion desplegada. Las pruebas realizadas fueron realizadas con init Chaos el cual al establecer neustra prueba nos dara de baja el servicio pero gracias a Kubernetes este se levanta por si solo en poco tiempo.
> 


### CheekyMonkey
![image](https://user-images.githubusercontent.com/88942550/205560120-cff0986d-72c9-400a-8424-cde0e59f6c00.png)

### **Chaos toolkit **<br><br>

## Instalacion y version
![image](https://user-images.githubusercontent.com/91103822/205562790-3e3c9d65-e479-42dc-bf03-b59901ba0c75.png)

### init chaos
![image](https://user-images.githubusercontent.com/91103822/205562880-2e8536e9-feb8-41ce-bea0-047e6923165b.png)





