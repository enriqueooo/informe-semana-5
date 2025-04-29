# Práctica: Creación de un sitio WordPress con contenedores Docker

## 1. Título  
**Creación de contenedores WordPress, MySQL y phpMyAdmin utilizando Docker**

## 2. Tiempo de duración  
**90 minutos**

## 3. Fundamentos  

En esta práctica aprenderé a crear un entorno de desarrollo web completo basado en WordPress, utilizando Docker para contenerizar los servicios necesarios. WordPress es un sistema de gestión de contenidos (CMS) ampliamente utilizado para crear sitios web y blogs, mientras que MySQL sirve como motor de base de datos. phpMyAdmin permite administrar MySQL mediante una interfaz web amigable.

Se utilizará Docker para levantar contenedores individuales que trabajarán de forma conectada gracias a una red personalizada, simulando un entorno de servidor real sin necesidad de instalar los servicios directamente en el sistema operativo anfitrión.

## 4. Conocimientos previos

Para realizar esta práctica, se recomienda tener nociones sobre:

- Fundamentos y comandos básicos de Docker.
- Funcionamiento de servicios como WordPress, MySQL y phpMyAdmin.
- Redes en Docker.
- Variables de entorno en contenedores.

## 5. Objetivos a alcanzar

- Crear una red personalizada en Docker para la comunicación entre servicios.
- Crear un volumen para persistir los datos de la base de datos.
- Ejecutar contenedores para MySQL, phpMyAdmin y WordPress.
- Acceder a WordPress y phpMyAdmin desde el navegador para realizar pruebas.

## 6. Equipo necesario

- Un computador con **Docker** instalado o acceso a un entorno como **Docker Playground**.
- Conexión a internet.
- Navegador web para acceder a WordPress y phpMyAdmin.

## 7. Material de apoyo

- Documentación oficial de Docker: [https://docs.docker.com/](https://docs.docker.com/)
- Documentación de WordPress: [https://wordpress.org/support/](https://wordpress.org/support/)
- Documentación de MySQL: [https://dev.mysql.com/doc/](https://dev.mysql.com/doc/)
- Documentación de phpMyAdmin: [https://www.phpmyadmin.net/docs/](https://www.phpmyadmin.net/docs/)

---

## 8. Procedimiento

### Parte 1: Crear red y volumen

**Paso 1: Crear una red personalizada**

```bash
docker network create wordpress-net
## Paso 2: Crear un volumen para los datos de MySQL
```
Para asegurar que los datos de MySQL persistan incluso si el contenedor se elimina, creamos un volumen de Docker:

```bash
docker volume create mysql-data
```
## Parte 2: Crear los contenedores

### Paso 3: Crear el contenedor de MySQL

Vamos a crear un contenedor de MySQL con las credenciales necesarias y vinculando el volumen creado previamente (`mysql-data`) para persistir los datos:

```bash
docker run -d \
  --name mysql-container \
  --network wordpress-net \
  -e MYSQL_ROOT_PASSWORD=rootpassword \
  -e MYSQL_DATABASE=wordpress \
  -e MYSQL_USER=wordpressuser \
  -e MYSQL_PASSWORD=wordpresspassword \
  -v mysql-data:/var/lib/mysql \
  mysql:5.7
```
### Paso 4: Crear el contenedor de phpMyAdmin

Para facilitar la administración de la base de datos MySQL, se puede usar phpMyAdmin, una interfaz web accesible desde el navegador:

```bash
docker run -d \
  --name phpmyadmin-container \
  --network wordpress-net \
  -e PMA_HOST=mysql-container \
  -e PMA_PORT=3306 \
  -p 8080:80 \
  phpmyadmin/phpmyadmin
```
### Paso 5: Crear el contenedor de WordPress

Ahora creamos el contenedor de WordPress y lo conectamos a la base de datos MySQL definida anteriormente:

```bash
docker run -d \
  --name wordpress-container \
  --network wordpress-net \
  -e WORDPRESS_DB_HOST=mysql-container:3306 \
  -e WORDPRESS_DB_NAME=wordpress \
  -e WORDPRESS_DB_USER=wordpressuser \
  -e WORDPRESS_DB_PASSWORD=wordpresspassword \
  -p 8081:80 \
  wordpress:latest
```

## Parte 3: Acceso a interfaces web

### Paso 6: Acceder desde el navegador

Una vez que los contenedores están en ejecución, puedes acceder a las interfaces web desde tu navegador:

- **WordPress**:  
  [http://localhost:8081](http://localhost:8081)

- **phpMyAdmin**:  
  [http://localhost:8080](http://localhost:8080)

Desde estas interfaces puedes configurar tu sitio web en WordPress y gestionar la base de datos MySQL fácilmente a través phpMyAdmin.

## 9. Resultados esperados

- WordPress debe mostrar su asistente de instalación al acceder por navegador.
- phpMyAdmin debe conectarse correctamente al contenedor de MySQL.
- Es posible crear tablas y gestionar la base de datos desde phpMyAdmin.
- Todos los contenedores deben estar corriendo en la misma red y poder comunicarse sin problemas.

## 10. Bibliografía

- Docker Documentation. (2024). [https://docs.docker.com/](https://docs.docker.com/)
- WordPress Support. (2024). [https://wordpress.org/support/](https://wordpress.org/support/)
- MySQL Documentation. (2024). [https://dev.mysql.com/doc/](https://dev.mysql.com/doc/)
- phpMyAdmin Documentation. (2024). [https://www.phpmyadmin.net/docs/](https://www.phpmyadmin.net/docs/)

## 11. Enlace del audio

```

