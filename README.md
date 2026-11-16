# Grupo 7 - Sitio web HTML sobre servicios de correo electrónico

Actividad práctica de **Redes y Comunicaciones IP**. Sitio web desarrollado en HTML puro, alojado en GitHub y desplegado mediante contenedores con Nginx y Docker.

## Integrantes

- Brenda Guzmán
- Santiago López

## Descripción

Sitio web hecho únicamente con HTML que desarrolla el tema asignado al grupo sobre servicios de correo electrónico. En sus secciones se explican las funciones generales de los clientes y servidores de correo, las diferencias entre SMTP e IMAP, el papel de Postfix y Dovecot, el recorrido ilustrativo de un mensaje y su relación con la capa 7 del Modelo OSI.

| Elemento | Detalle |
|---|---|
| Tema | Servicios de correo electrónico |
| Herramientas de referencia | Postfix y Dovecot |
| Protocolos principales | SMTP e IMAP |
| Transporte habitual | TCP |

También incluye una tabla de puertos habituales, consideraciones de seguridad, fuentes técnicas de consulta y una página individual por cada integrante con su biografía y resumen de lo aprendido en el curso. El contenedor Docker de este repositorio utiliza Nginx para publicar las páginas HTML, por lo que no instala ni configura Postfix o Dovecot.

## Estructura del proyecto

```text
Grupo7_HTML/
├── README.md
├── Dockerfile
├── docker-compose.yml
├── index.html
├── img/
│   ├── brenda.jpeg
│   ├── brenda.svg
│   ├── logo_u.png
│   ├── modelo_osi.jpg
│   ├── Recorrido.jpg
│   └── santiago.svg
└── integrantes/
    ├── brenda-guzman.html
    └── santiago-lopez.html
```

## Cómo ejecutar el proyecto con Docker

### Requisitos

- [Git](https://git-scm.com/)
- [Docker](https://www.docker.com/)

### Pasos con Docker

1. Clonar el repositorio y entrar a la carpeta del proyecto

```bash
git clone https://github.com/brendaguzman05/Grupo7_HTML.git
cd Grupo7_HTML
```

2. Construir la imagen

```bash
docker build -t grupo7-sitio-html .
```

3. Ejecutar el contenedor

```bash
docker run -d -p 8001:80 --name grupo7-sitio-html grupo7-sitio-html
```

4. Abrir en el navegador

```text
http://localhost:8001
```

### Alternativa con Docker Compose

Desde la carpeta donde se encuentran `docker-compose.yml` y `Dockerfile`, ejecutar

```bash
docker compose up -d --build
```

El sitio también quedará disponible en `http://localhost:8001`.

### Comprobar el estado y consultar los registros

Para verificar que el servicio esté activo

```bash
docker compose ps
```

Para consultar los registros del contenedor

```bash
docker compose logs -f
```

Para salir de la visualización de registros, presionar `Ctrl + C`. Esto no detiene el contenedor.

### Detener el servicio

```bash
docker compose down
```

Si se inició mediante el comando `docker run` en lugar de Docker Compose, detener y eliminar el contenedor con

```bash
docker stop grupo7-sitio-html
docker rm grupo7-sitio-html
```

### Aplicar cambios realizados en los archivos

Cuando se modifica el contenido del sitio y se está utilizando Docker Compose, reconstruir y levantar nuevamente el servicio

```bash
docker compose up -d --build
```

## Repositorio

https://github.com/brendaguzman05/Grupo7_HTML

## Licencia

Uso académico y educativo.
