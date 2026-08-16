---
layout: default
title: Justificación tecnológica
nav_order: 3
---

# 🛠️ Justificación tecnológica

En esta sección documentamos las decisiones técnicas tomadas para la construcción del microservicio core del club, asegurando que cada herramienta elegida aporte valor real al desarrollo y mantenimiento del producto.

## Lenguajes y frameworks

Dado que este microservicio concentra la mayor complejidad de dominio y volumen de tablas de la aplicación, la selección tecnológica se centró en la robustez estructural y la escalabilidad:

* **Python:** Elegido por su versatilidad y la claridad que aporta al modelado de reglas de negocio complejas y extensas.
* **FastAPI:** Seleccionado como framework web por su alto rendimiento asíncrono. Permite estructurar una gran cantidad de controladores de forma limpia y autogenera la documentación Swagger/OpenAPI necesaria para el resto de los servicios.
* **SQLAlchemy y Alembic:** Pilares fundamentales para el manejo del modelo relacional masivo (socios, reservas, disciplinas, finanzas) y la ejecución controlada de migraciones de base de datos a lo largo del ciclo de vida del producto.
* **Cloudinary:** Integrado para la gestión y almacenamiento optimizado de archivos multimedia e imágenes (como las fotos de perfil de los socios).
* **Pytest:** Nuestro framework de pruebas, esencial para asegurar mediante una batería masiva de tests que la interacción entre los múltiples submódulos del club no genere efectos secundarios indeseados.
* **Docker y Docker Compose:** La contenerización es indispensable en nuestra arquitectura. Nos permite aislar el microservicio y garantizar la paridad exacta entre entornos (desarrollo, *staging* y producción).

## Integración y despliegue continuo (CI/CD)

La implementación de pipelines de CI/CD es fundamental en el microservicio para garantizar entregas ágiles y seguras. Nos permite automatizar la ejecución de pruebas y el despliegue a los distintos entornos, reduciendo el error humano y acelerando el *time-to-market*.

## Pruebas unitarias y Code Coverage

Para asegurar la robustez y estabilidad del código, mantenemos un estándar estricto de calidad:

* Se ha implementado una gran cantidad de pruebas unitarias cubriendo los casos de uso principales y casos borde.
* Mantenemos un **estricto nivel de Code Coverage** (cobertura de código) fijado en un mínimo del **90%**, el cual es validado automáticamente en cada Pull Request mediante nuestro pipeline.

## Documentación integral

Utilizamos **JustTheDocs** para mantener esta documentación viva, versionada junto con el código y fácilmente accesible para cualquier miembro del equipo. Esto centraliza el conocimiento y reduce los cuellos de botella en la comunicación.
