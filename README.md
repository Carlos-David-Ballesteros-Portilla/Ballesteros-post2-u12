# ballesteros-post2-u12

![CI/CD Status](https://github.com/carlosdavidballesterosportilla/ballesteros-post2-u12/actions/workflows/ci.yml/badge.svg)

## Descripción

Aplicación Spring Boot contenedorizada con Docker y desplegada en Railway, con pipeline CI/CD automatizado mediante GitHub Actions.

## Pipeline CI/CD

El pipeline se activa automáticamente en cada push a `main` y realiza:
1. Compilación con Maven y ejecución de pruebas unitarias
2. Generación de reporte de cobertura JaCoCo
3. Construcción de imagen Docker con multi-stage build
4. Publicación de la imagen en Docker Hub con tags `latest` y `sha-<commit>`

## Imagen Docker

```
docker pull carlosdavidballesterosportilla/mi-spring-app:latest
```

## GitHub Secrets requeridos

| Secret | Descripción |
|---|---|
| `DOCKERHUB_USERNAME` | Nombre de usuario de Docker Hub |
| `DOCKERHUB_TOKEN` | Access Token generado en Docker Hub (no la contraseña) |

Ruta para configurarlos: `Settings → Secrets and variables → Actions → New repository secret`

## Ejecutar localmente con Docker Compose

```bash
docker compose up -d --build
```

Verificar estado:

```bash
curl http://localhost:8080/actuator/health
```

Detener los servicios:

```bash
docker compose down
```