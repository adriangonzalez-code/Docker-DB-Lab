# Docker DataBase Lab

Este repositorio contiene configuraciones y comandos para levantar distintos motores de bases de datos en contenedores Docker. El objetivo es facilitar el desarrollo sin necesidad de instalar cada motor localmente.

## Requisitos

* Docker instalado en tu máquina.
* Conexión a internet para descargar las imágenes oficiales.
* Conocimientos básicos de terminal y Docker.

## Motores disponibles

### MySQL 5.7
```bash
docker run -d --name mysql5 -e MYSQL_ROOT_PASSWORD=rootpass -e MYSQL_DATABASE=devdb -p 3307:3306 mysql:5.7
```

### MySQL 8
```bash
docker run -d --name mysql8 -e MYSQL_ROOT_PASSWORD=rootpass -e MYSQL_DATABASE=devdb -p 3308:3306 mysql:8
```

### MariaDB
```bash
docker run -d --name mariadb -e MARIADB_ROOT_PASSWORD=rootpass -e MARIADB_DATABASE=devdb -p 3309:3306 mariadb:latest
```

### MongoDB

```bash
docker run -d --name mongodb -e MONGO_INITDB_ROOT_USERNAME=root -e MONGO_INITDB_ROOT_PASSWORD=rootpass -p 27017:27017 mongo:latest
```

### Oracle XE
```bash
docker run -d --name oracle-xe -p 1521:1521 -p 5500:5500 -e ORACLE_PWD=rootpass gvenzl/oracle-xe
```

### SQL Server
```bash
docker run -d --name sqlserver -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=RootPass123!' -p 1433:1433 mcr.microsoft.com/mssql/server:2019-latest
```

### PostgreSQL
```bash
docker run -d --name postgres -e POSTGRES_PASSWORD=rootpass -e POSTGRES_DB=devdb -p 5432:5432 postgres:latest
```

## Conexión desde aplicaciones
* Host: `localhost`
* Puerto: según cada motor (ej. 3307 para MySQL 5, 5432 para PostgreSQL).
* Usuario y contraseña: definidos en las variables de entorno.
* Base de datos inicial: `devdb` (cuando aplica).

## Administración

* Ver contenedores activos:

```bash
docker ps
```

* Detener un contenedor:

```bash
docker stop <nombre>
```

* Iniciar un contenedor:

```bash
docker start <nombre>
```

## Notas
* Usa contraseñas seguras en proyectos reales.
* Estos entornos son solo para desarrollo y pruebas.
* Puedes extender este repo con un archivo docker-compose.yml para levantar todos los servicios juntos.
