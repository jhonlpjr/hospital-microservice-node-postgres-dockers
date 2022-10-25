## Description

Se desarrolló un microservicio para pacientes de un hospital, que pueda registrar un nuevo paciente para su atención y que tambien pueda listar los pacientes ya registrados.
Para el consumo del microservicio se desarrollo un API-GATEWAY con peticiones HTTP, que pueda facilitar el acceso como tal desde cualquier cliente que permita realizar peticiones de Api Rest como GET y POST, ya que el microservicio desarrollado se comunica por messages cmd a nivel TCP (Tambien se comunican a nivel de events, coles, sockets, etc. ).
El microservicio está conectado a una base de datos: hospital, en la tabla: patient.
Las tecnologías utilizadas para el proyecto son: 

    * Node.js para el Microservicio y para el Api-Gateway
    * PostgreSql para la base de datos
    * Docker para los contenedores, que nos permitirán levantar las partes del proyecto de manera independiente y de forma escalable sin necesidad de depender del host en donde se encuentre descargado.

## Configuration

**LUEGO DE CLONAR O DESCARGAR EL PROYECTO**

**Recordar que cada submodule debe estar en la última versión o en la rama master, para que este con los últimos cambios funcionales actualzados.**

**Para configurar el microservicio**

En la raíz del proyecto, ubicarse con la carpeta *patient_microservice*.
Ahí se configurarán las credenciales de la base de datos en el archivo: .env, hay un archivo pre existente llamado: .env.example, el cual tiene el ejemplo de como dejar las credenciales. En *DB_HOST*, poner de preferencia el ip de la máquina local y no localhost, ya que en ocasiones genera erorres por configuración restante de la misma pc o laptop en que se descargo el proyecto.
```bash
DB_HOST=YOUR.IP,
```
En caso se requiera, se configurará los demás parámetros pero de preferencia dejarlos como tal.

**Para configurar el api-gateway**

En la raíz del proyecto, ubicarse con la carpeta api_gateway.
Se configurarán las credenciales para consumir el microservicio en el archivo: .env, hay un archivo pre existente llamado: .env.example, el cual tiene el ejemplo de como dejar las credenciales. En *MS_HOST*, poner de preferencia el ip de la máquina local y no localhost, ya que en ocasiones genera erorres por configuración restante de la misma pc o laptop en que se descargo el proyecto.
```bash
MS_HOST=YOUR.IP,
```
En caso se requiera, configurará los demás parámetros pero de preferencia dejarlos como tal.

## Installation & Deploy

**Primero la Base de Datos**

Se Levantará el contenedor de postgresql, el cual ya viene preconfigurado en su respectivo archivo docker-compose.yml, para ello nos utilizaremos la terminal de nuestra preferencia y teniendo previamente instalado docker en nuestra máquica host, nos ubicaremos en la raíz del proyecto y luego la carpeta database.
Ahí ejecutaremos el siguiente comando:

```bash
$ docker-compose up
```

Esto instalará la imagen del contenedor y desplegará nuestra base de datos preconfigurada, podemos verificar las credenciales si deseamos en el archivo docker-compose.yml .

*Para reiniciar el contenedor:*
```bash
$ docker restart postgresql
```

*Para dar de baja el contenedor:*
```bash
$ docker-compose down
```

**Luego el microservicio y el api-gateway que lo consumirá y lo mostrará para su consumo externo mediante peticiones HTTP.**

Utilizaremos la terminal de nuestra preferencia y teniendo previamente instalado docker en nuestra máquica host, nos ubicaremos en la raíz del proyecto.

Ahí ejecutaremos el siguiente comando:
```bash
$ docker-compose up
```
Este instalará y/o actualziará las dependencias de ambas partes, luego levantará los contenedores respectivos de node para cada uno, luego de ello ya podremos consumir nuestro microsevicio de paciente, el cual se podrá accede mediante dos enpoints del api-gateway, el cual consume el microsevicio por dentro.

## Swagger

**Para acceder al Swagger (Api Documentation)**

*Debe acceder  a la dirección de su máquina local o a localhost y ubicarse en el puerto 8080 , ahí añadir la ruta : /docs*

Ejemplo: (https://localhost:8080/docs)

*Ahí se podrá ver todos los endpoints, parámetros de uso, ejemplos de como se podrían usar los request y como llegarían los posibles responses.*

## Unit Test

**Para correr las pruebas unitarias:**

*Ubicarse en la carpeta raíz de api-gateway o de patient-microservice con la terminal de su preferencia y ejecutar el siguiente comando:*
```bash
# unit tests
$ npm run test
```

## Support

- Soporte - [Jonathan Reyna](jhonlpjr@gmail.com)

## About

- Autor - [Jonathan Reyna](https://github.com/jhonlpjr)

## License

Esta Api es de [Jonsnow](LICENSE).