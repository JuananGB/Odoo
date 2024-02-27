# Odoo en Docker Compose

Este archivo de configuración Docker Compose establece un entorno de desarrollo para Odoo utilizando PostgreSQL como base de datos. Define dos servicios: "web" y "mydb".

## Prerrequisitos

Antes de utilizar esta configuración, asegúrate de tener Docker y Docker Compose instalados en tu sistema.

- [Guía de Instalación de Docker](https://docs.docker.com/get-docker/)
- [Guía de Instalación de Docker Compose](https://docs.docker.com/compose/install/)

## Configuración

La configuración consta de dos servicios:

### 1. Servicio web

- **Imagen**: `odoo:16.0`
- **Puertos**:
    - Host: `8069`
    - Contenedor: `8069`
- **Variables de Entorno**:
    - `HOST`: `mydb`
    - `USER`: `odoo`
    - `PASSWORD`: `myodoo`
- **Dependencias**: Dependiente de la disponibilidad del servicio "mydb".

### 2. Servicio mydb

- **Imagen**: `postgres:15`
- **Variables de Entorno**:
    - `POSTGRES_DB`: `postgres`
    - `POSTGRES_USER`: `odoo`
    - `POSTGRES_PASSWORD`: `myodoo`

## Uso

1. **Clonar Repositorio**: Clona este repositorio en tu máquina local.

2. **Navegar al Directorio**: Navega al directorio que contiene el archivo `docker-compose.yml`.

3. **Iniciar Servicios**: Ejecuta el siguiente comando para iniciar los servicios de Odoo y PostgreSQL:

   ```bash
   docker-compose up -d
