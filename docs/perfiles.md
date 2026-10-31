Este proyecto se puede configurar para utilizar distintas bases de datos asi como diferente capa de repositorio:

Para la capa de repositorios se puede utilizar
  - Spring JPA, Spring JDBC , Spring Data JPA
  - 
        Para utilizar Spring jpa, utiliza: jpa
        Para utilizar Spring JDBC, utiliza: jdbc
        Para utilizar Spring Data JPA, utiliza: spring-data-jpa

Para la base de datos se pueden configurar los siguientes motores
  - H2, HSQL, MySQL, PostgreSQL
  -
        Para utilizar HSQL : hsqldb
        Para utilizar MySQL : mysql
        Para utilizar PostgreSQL : postgres
        Para utilizar H2 : h2

Ambas propiedades se utilizan en el archivo de propiedades application.properties
Ejemplo:

        spring.profiles.active=mysql,spring-data-jpa 

## Base de datos H2

Por default el proyecto utiliza H2 base de datos en memoria:

 - No se requiere configuracón adicional
 - El esquema de base de datos y datos de prueba son cargados automaticamente de src/main/resources/db/h2/ 
 - Se puede acceder a la consola H2 para inspeccionar la base de datos
   - Despues de correr la aplicación:    

     Abre la consola H2 en tu navegador:
     URL: http://localhost:9966/petclinic/h2-console
     JDBC URL: jdbc:h2:mem:petclinic
     Username: sa
     Password: (dejarlo en blanco)    

## Base de datos HSQLDB 

La base de datos HSQLDB trabaja similar a la base H2 como una base de datos en memoria
Se necesita modificar los siguientes valores en el archivo de propiedades application.properties

spring.profiles.active=hsqldb,spring-data-jpa

## Base de datos MySQL

Modificar application.properties:

spring.profiles.active=mysql,spring-data-jpa

Iniciar MySQL usando Docker:

docker run -e MYSQL_USER=petclinic -e MYSQL_PASSWORD=petclinic -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=petclinic -p 3306:3306 mysql:8.4

## Base de datos  PostgreSQL

Modificar application.properties:

spring.profiles.active=postgres,spring-data-jpa

Iniciar  PostgreSQL usando Docker:

docker run -e POSTGRES_USER=petclinic -e POSTGRES_PASSWORD=petclinic -e POSTGRES_DB=petclinic -p 5432:5432 postgres:16.3

## Usando Docker 

En lugar de ejecutar contenedores manualmente puedes ejecutar la aplicacion y la base de datos utilizando docker-compose.yml
docker-compose --profile mysql up
docker-compose --profile postgres up





