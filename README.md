# Configuración de Servicios Docker

Este repositorio contiene la configuración de varios servicios usando Docker Compose. Cada servicio tiene su propio directorio con archivos de configuración.

## Servicios Disponibles

- **chatwoot**: Sistema de chat en vivo
- **evolution_api**: API de WhatsApp
- **filebrower**: Explorador de archivos web
- **n8n**: Herramienta de automatización
- **odoo18**: ERP Odoo 18
- **pgadmin**: Administrador de PostgreSQL
- **py_kms**: Servidor KMS para activación de Windows

## Configuración de Variables de Entorno

Todos los servicios incluyen archivos `.example` que debes copiar y configurar con tus valores reales.

### 1. PgAdmin
```bash
cd pgadmin
cp config.env.example config.env
# Edita config.env con tus valores
```

### 2. Py-KMS
```bash
cd py_kms
cp config.env.example config.env
# Edita config.env con tus valores
```

### 3. Chatwoot
```bash
cd chatwoot
cp stack.env.example stack.env
# Edita stack.env con tus valores
```

### 4. Evolution API
```bash
cd evolution_api
cp config.env.example config.env
# Edita config.env con tus valores
```

### 5. N8N
```bash
cd n8n
cp config.env.example config.env
# Edita config.env con tus valores
```

### 6. Odoo 18
```bash
cd odoo18
cp config.env.example config.env
# Edita config.env con tus valores
```

## Variables Importantes a Configurar

### URLs
- `FRONTEND_URL`: Tu dominio principal (ej: tu-dominio.com)

### Base de Datos
- `POSTGRES_USER`: Usuario de PostgreSQL
- `POSTGRES_PASSWORD`: Contraseña de PostgreSQL
- `POSTGRES_DB`: Nombre de la base de datos

### Servicios Específicos
- **PgAdmin**: `PGADMIN_DEFAULT_EMAIL`, `PGADMIN_DEFAULT_PASSWORD`
- **N8N**: `N8N_USER`, `N8N_PASS`
- **Evolution API**: `AUTHENTICATION_API_KEY`, `RABBITMQ_*`
- **Chatwoot**: `REDIS_PASSWORD`, `SECRET_KEY_BASE`

## Redes Docker

Los servicios están configurados para usar las siguientes redes:
- `caddy`: Red externa para el proxy reverso
- `driver_sql`: Red externa para conexiones de base de datos
- Redes específicas de cada servicio

## Uso

Para levantar un servicio específico:
```bash
cd nombre-del-servicio
docker-compose up -d
```

Para levantar todos los servicios:
```bash
# Desde el directorio raíz
docker-compose -f chatwoot/compose.yaml up -d
docker-compose -f evolution_api/compose.yaml up -d
# ... etc para cada servicio
```

## Seguridad

⚠️ **IMPORTANTE**: 
- Cambia todas las contraseñas por defecto
- Usa contraseñas seguras y únicas
- No subas los archivos `.env` al control de versiones
- Configura certificados SSL para producción

## Control de Versiones

El archivo `.gitignore` está configurado para ignorar automáticamente:
- Todos los archivos `.env`
- Archivos de configuración local
- Logs y archivos temporales
- Directorios de datos de Docker

Los archivos `.example` están incluidos en el repositorio para facilitar la configuración inicial.
