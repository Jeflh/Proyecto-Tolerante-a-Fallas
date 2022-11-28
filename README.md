# Proyecto-Tolerante-a-Fallas 
**Servidor de Minecraft**

Juan José Salazar Villegas
Paola Vanessa Del Río Gómez
Juen Emmanuel Fernández de Lara Hernández

## Insalar minikube
### winget install minikube
![image](https://user-images.githubusercontent.com/88942550/204116926-cd6494c2-d3ac-4fe9-a7c1-778d61c3c76d.png)


### minikube start
![image](https://user-images.githubusercontent.com/88942550/204116886-8838acba-b701-4759-82fc-33acdf2def74.png)

### Activar Hyper-V
#### Get-WindowsOptionalFeature -FeatureName Microsoft-Hyper-V-All -Online
![image](https://user-images.githubusercontent.com/91103822/204117028-8f48b677-cd19-4c8f-982a-88e44a3dad19.png)
![image](https://user-images.githubusercontent.com/88942550/204116988-c2c7a7a7-194e-4141-ac5b-0bd6d10e3790.png)


**Comando de creacion de nuestro Contenedor:**<br><br>
docker run -e EULA=TRUE -p 25565:25565 -v C:\Users\Salvi\Desktop\Minecraft-Docker\temp_data2:/data itzg/minecraft-server:latest

**Contenedor en Doker:**<br><br>
![image](https://user-images.githubusercontent.com/91103822/204116265-3ca4b3d9-8dde-4fb7-9aab-060a649a5bc6.png)
**Volumen:**<br><br>
![image](https://user-images.githubusercontent.com/91103822/204116282-8ebdce5a-3e8c-4290-9aaa-965294bee084.png)
**Creacion de Mundo:**<br><br>
![image](https://user-images.githubusercontent.com/91103822/204116295-d3e4a245-d4cb-4903-9afb-2d1bd929b62d.png)
**Contenido de servidor:**<br><br>
![image](https://user-images.githubusercontent.com/91103822/204116316-f42e18c3-9ce4-4482-b645-639e89197624.png)

**Configuración de Servidor en Minecraft:**<br><br>
![image](https://user-images.githubusercontent.com/91103822/204116533-b70af9d1-8d5d-4e48-b406-a20e5371e28e.png)
![image](https://user-images.githubusercontent.com/91103822/204116565-0be16f0d-9e98-42f8-939b-f6fff7721a9b.png)

**Pruebas:**<br><br>
![2022-11-26_20 32 40](https://user-images.githubusercontent.com/91103822/204116729-f06291ff-751b-4670-938d-d62650ab15df.png)
![2022-11-26_20 36 20](https://user-images.githubusercontent.com/91103822/204116730-535bcd2d-b5ed-4929-84a8-9da835017739.png)
![2022-11-26_20 01 00](https://user-images.githubusercontent.com/91103822/204116732-99e8e7ab-1fe6-44db-b069-abcf8bf4238c.png)
![image](https://user-images.githubusercontent.com/88942550/204116803-793a3018-12ce-473e-bf94-069e6be98aca.png)
![image](https://user-images.githubusercontent.com/91103822/204116673-b20b7a4a-c5ab-4811-8e50-294baa725925.png)

