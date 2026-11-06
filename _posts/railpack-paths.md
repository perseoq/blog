---
title: railpack static paths
date: 2026-11-05
author: Rodrigo Quintanar
---


# Railpack: rutas estáticas

Una precisión importante: Railpack no ofrece una variable universal `ROOT_DIR` para todos los lenguajes. Algunas tecnologías tienen variables específicas y otras requieren configuración mediante `railpack.json`, `Staticfile` o un `Caddyfile`.

## 1. PHP

| Framework     | Variable Railpack       | Valor          |
| ------------- | ----------------------- | -------------- |
| CodeIgniter 4 | `RAILPACK_PHP_ROOT_DIR` | `/app/public`  |
| Laravel       | `RAILPACK_PHP_ROOT_DIR` | `/app/public`  |
| Symfony       | `RAILPACK_PHP_ROOT_DIR` | `/app/public`  |
| CakePHP       | `RAILPACK_PHP_ROOT_DIR` | `/app/webroot` |
| Yii2          | `RAILPACK_PHP_ROOT_DIR` | `/app/web`     |
| Drupal        | `RAILPACK_PHP_ROOT_DIR` | `/app/web`     |
| WordPress     | `RAILPACK_PHP_ROOT_DIR` | `/app`         |

Las rutas de CakePHP, Yii2, Drupal y WordPress son convenciones de sus proyectos, no valores automáticos garantizados por Railpack.&#x20;

![image](https://www.google.com/s2/favicons?domain=https://railpack.com\&sz=32)

Railpack Docs



## 2. JavaScript / TypeScript

| Framework       | Variable Railpack           | Valor                 |
| --------------- | --------------------------- | --------------------- |
| React + Vite    | `RAILPACK_STATIC_FILE_ROOT` | `dist`                |
| Vue + Vite      | `RAILPACK_STATIC_FILE_ROOT` | `dist`                |
| Angular         | `RAILPACK_STATIC_FILE_ROOT` | `dist/nombre/browser` |
| Astro estático  | `RAILPACK_STATIC_FILE_ROOT` | `dist`                |
| Svelte estático | `RAILPACK_STATIC_FILE_ROOT` | `build` o `dist`      |
| Next.js         | No aplica                   | Servidor Node         |
| Nuxt SSR        | No aplica                   | Servidor Node         |
| Express         | No aplica                   | Servidor Node         |
| NestJS          | No aplica                   | Servidor Node         |

Para las aplicaciones estáticas, `RAILPACK_STATIC_FILE_ROOT` sí está documentada. Para SSR, no debes configurar un document root estático: se utiliza el servidor de la aplicación.&#x20;

![image](https://www.google.com/s2/favicons?domain=https://railpack.com\&sz=32)

Railpack Docs+2



## 3. Python

| Framework | Variable Railpack                   | Valor     |
| --------- | ----------------------------------- | --------- |
| Django    | No existe variable de document root | No aplica |
| Flask     | No existe variable de document root | No aplica |
| FastAPI   | No existe variable de document root | No aplica |

Django tiene una variable específica de Railpack para identificar su aplicación WSGI:

```
RAILPACK_DJANGO_APP_NAME=myproject.wsgi
```

No es una variable de document root.&#x20;

![image](https://www.google.com/s2/favicons?domain=https://github.com\&sz=32)

GitHub



## 4. Otros lenguajes

| Framework         | Variable Railpack de document root | Configuración              |
| ----------------- | ---------------------------------- | -------------------------- |
| Ruby on Rails     | No existe                          | Servidor Rails             |
| ASP.NET Core      | No existe                          | `wwwroot`                  |
| Spring Boot       | No existe                          | Recursos estáticos         |
| Go (Gin/Fiber)    | No existe                          | Configuración del servidor |
| Rust (Actix/Axum) | No existe                          | Configuración del servidor |
| Phoenix           | No existe                          | `priv/static`              |

Railpack permite configurar estos proveedores, pero no publica una variable universal para establecer su document root.&#x20;

![image](https://www.google.com/s2/favicons?domain=https://railpack.com\&sz=32)

Railpack Docs+1



## 5. Variables de configuración relevantes

| Variable                    | Función                          |
| --------------------------- | -------------------------------- |
| `RAILPACK_PHP_ROOT_DIR`     | Document root PHP                |
| `RAILPACK_STATIC_FILE_ROOT` | Directorio de archivos estáticos |
| `RAILPACK_PHP_EXTENSIONS`   | Extensiones PHP                  |
| `RAILPACK_DJANGO_APP_NAME`  | Aplicación WSGI de Django        |
| `RAILPACK_PYTHON_VERSION`   | Versión de Python                |
| `RAILPACK_BUILD_CMD`        | Comando de construcción          |
| `RAILPACK_START_CMD`        | Comando de inicio                |

Documentación oficial: [Railpack Environment Variables](https://railpack.com/config/environment-variables/?utm_source=chatgpt.com).

Conclusión: para tus despliegues en Dokploy, las dos variables que debes tener especialmente presentes son `RAILPACK_PHP_ROOT_DIR` y `RAILPACK_STATIC_FILE_ROOT`. Las demás tecnologías normalmente necesitan configurar su servidor de aplicaciones, no una ruta pública de Railpack.
