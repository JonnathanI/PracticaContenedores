# PracticaContenedores

# Informe de Configuración de Contenedores Docker para PostgreSQL y pgAdmin4

## Tiempo de Duración
- Aproximadamente 10-15 minutos, dependiendo de la velocidad de descarga de las imágenes de Docker.

## Fundamentos
El propósito de esta práctica es configurar un entorno de base de datos utilizando Docker, que permita la administración de una base de datos PostgreSQL y la visualización y gestión de datos mediante pgAdmin4.

## Conocimientos Previos
- Conceptos básicos de Docker y contenedores.
- Familiaridad con PostgreSQL y la herramienta pgAdmin.
- Conocimiento básico de redes y administración de bases de datos.

## Objetivos a Alcanzar
1. Ejecutar una base de datos PostgreSQL en un contenedor Docker.
2. Configurar pgAdmin4 en otro contenedor Docker para gestionar la base de datos.
3. Conectar ambos contenedores en una red Docker personalizada para facilitar la comunicación.

## Equipo Necesario
- Computadora con Docker instalado.

## Material de Apoyo
- [Documentación de Docker](https://docs.docker.com/)
- [Documentación de PostgreSQL](https://www.postgresql.org/docs/)
- [Documentación de pgAdmin4](https://www.pgadmin.org/docs/)

## Procedimiento

1. **Ejecutar el contenedor de PostgreSQL**  
   Ejecuta el siguiente comando en la terminal para lanzar el contenedor de PostgreSQL con el nombre `dbpost` y la contraseña `admin`:
   ```bash
   docker run -d --name dbpost -e POSTGRES_PASSWORD=admin -p 5432:5432 postgres
   ```
2. **Ejecutar el contenedor de pgAdmin4**
   Ejecuta el siguiente comando para lanzar el contenedor de pgAdmin4 con la dirección de correo y contraseña predeterminada:
   ```bash
   docker run -d --name pgadmin -p 8090:80 -e PGADMIN_DEFAULT_EMAIL=jjinaguazo@sudamericano.edu.ec -e PGADMIN_DEFAULT_PASSWORD=admin dpage/pgadmin4
   ```
3. **Verificar los contenedores en ejecución**
   Usa el siguiente comando para verificar que los contenedores están corriendo:
   ```bash
   docker ps
   ```
4. **Crear y conectar la red Docker**
   Crea una red llamada redPractica y conecta ambos contenedores a esta red:
   ```bash
   docker network create --attachable redPractica
   docker network connect redPractica dbpost
   docker network connect redPractica pgadmin
   ```
5. **Comprobar si la Practica Funciono**
   - En este Caso se Verifico Ingresando al Puerto que se defini para PgAdmin que es el 8089:80.
   ![image](https://github.com/user-attachments/assets/3be24108-a199-4589-bb63-1001d525b30f)
   
   -  Al Momento de Ingresar nos va a Mostrar una Pantalla de Logeo, el caul el Usuario y la Contraseña el cual se definio en el paso 2.
   ![image](https://github.com/user-attachments/assets/6443b851-c3da-40e5-8a8b-43c99658bcf6)
   
   -  Despues de loguearte se hace la conexion entre los 2 Contenedore mediante la opcion que dice Agregar un Nuevo Servidor.
   ![image](https://github.com/user-attachments/assets/b3b031b9-cde2-46c2-837c-7ecefd5a3013)
   
   -  Configuracion
       1. Se da un Nombre al Servidor
           ![image](https://github.com/user-attachments/assets/fce73bc6-8de1-4f62-a245-59da22527d66)
       2. Se Ingresa el Nombre de Otro Servidor que es Postgres y la base
           ![image](https://github.com/user-attachments/assets/5df087d9-2a47-4ddc-8b8c-89036f35b745)

   - Por Ultimo despues de Haber echa la conexion entre estos Contenedores se puede comprobar Creando Una Tabla
         ![image](https://github.com/user-attachments/assets/f0b4b284-5ef0-492e-a825-0e60a45abebd)

6. **Resultados Esperados**
   . PostgreSQL y pgAdmin4 ejecutándose en contenedores Docker.
   . Comunicación exitosa entre los contenedores a través de la red redPractica.
   . Acceso a pgAdmin4 desde un navegador en http://localhost:8090 para gestionar la base de datos de PostgreSQL.
7. **Bibliografia**
   . Docker. “Get Started with Docker.” https://docs.docker.com/get-started/
   . PostgreSQL Documentation. https://www.postgresql.org/docs/
   . pgAdmin Documentation. https://www.pgadmin.org/docs/
         




   
