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
