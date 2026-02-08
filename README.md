# SE-ProjectUG
Proyecto de Ingeniería de Software Avanzada.

## 1. Elección del proyecto

El proyecto seleccionado para este trabajo es **django-realworld-example-app**, una implementación backend del RealWorld / Conduit App utilizando Django y Django REST Framework.

La razón principal para elegir este proyecto es que representa un backend realista, con múltiples dominios bien definidos, interacciones entre usuarios y reglas de negocio no triviales. A diferencia de proyectos puramente CRUD, este repositorio permite analizar arquitectura, deuda técnica, separación de responsabilidades y aplicar conceptos como Domain-Driven Design (DDD) de forma práctica.

Además, el proyecto cuenta con una estructura modular basada en apps, lo que facilita la identificación de Bounded Contexts y la trazabilidad entre requerimientos funcionales y código.

## 2. Tareas realizadas (Tasks)

Esta sección describe las tareas realizadas durante el Delivery #1: Discovery & Reverse Engineering, explicando cómo cada una contribuyó a entender el sistema, su dominio y su estructura interna.

### 2.1 Task #1 – Onboarding Log

El objetivo de esta tarea fue documentar el proceso real de onboarding al proyecto, identificando problemas, fricciones y decisiones técnicas necesarias para lograr ejecutar el sistema correctamente.

Durante esta fase se identificaron múltiples puntos de fricción técnicos, principalmente relacionados con:

- Uso de versiones antiguas de Python (3.5.x / 3.6.x) y Django (1.10.5).
- Incompatibilidades al intentar ejecutar el proyecto con versiones modernas.
- Inconsistencias entre la estructura real del repositorio y las rutas mencionadas en el README.md.
- Falta inicial de claridad sobre cómo interactuar con el backend una vez levantado.

Para resolver estos problemas, se tomó la decisión de utilizar Docker como mecanismo de aislamiento del entorno, permitiendo ejecutar el proyecto con versiones compatibles sin afectar el sistema local. Además, se utilizó django-extensions para descubrir los endpoints disponibles y validar que el proyecto corresponde a una API backend funcional.

Este onboarding permitió no solo levantar el proyecto, sino también entender su naturaleza, límites y dependencias, sentando la base para el análisis posterior del dominio.

### 2.2 Task #2 – AI-Driven Discovery & Context Map

En esta tarea se realizó un análisis asistido por LLMs (Gemini, Copilot y ChatGPT) para descubrir la funcionalidad del sistema y su estructura de dominio. Aunque se consultaron múltiples herramientas, se seleccionó la respuesta de ChatGPT por considerarse la más completa y consistente con el código.

A partir de este análisis se identificó que el proyecto es una API REST backend que implementa el dominio de una plataforma tipo Medium, permitiendo:

- Gestión de usuarios y autenticación
- Publicación de artículos
- Interacción social entre usuarios
- Comentarios y clasificación por tags

Con base en la estructura real de la codebase (apps de Django), se identificaron los Bounded Contexts principales y se construyó un Context Map, donde cada contexto corresponde directamente a una app del proyecto:

- Users
- Profiles
- Articles
- Comments
- Tags

Este mapa permitió visualizar claramente las relaciones entre contextos (Shared Kernel, Partnership, Customer/Supplier y dependencias simples), alineando el análisis conceptual con la implementación real del sistema.

### 2.3 Task #3 – Backlog Recovery

La tercera tarea consistió en la recuperación del backlog funcional del sistema, a partir de los Bounded Contexts previamente identificados.

Para esta tarea se generó una lista de historias de usuario existentes, utilizando el formato clásico:

> Como…
> Quiero…
> Para…

Cada historia de usuario fue cuidadosamente trazada hasta módulos y archivos específicos del código, garantizando que no se tratara de funcionalidades hipotéticas, sino de capacidades reales ya implementadas en el sistema.

Las historias cubren todos los contextos principales del dominio:

- Usuarios (registro y autenticación)
- Perfiles (visualización y seguimiento)
- Artículos (publicación y favoritos)
- Comentarios (creación y eliminación)
- Tags (listado y asociación)

Este backlog recuperado sirve como un puente entre el dominio y la implementación técnica, y será utilizado como referencia para análisis posteriores de calidad, deuda técnica y refactorización.

## 3. Relación entre las tareas

Las tres tareas están directamente conectadas entre sí:

- El Onboarding Log permitió ejecutar y explorar el sistema.
- El AI-Driven Discovery & Context Map transformó esa exploración en conocimiento estructurado del dominio.
- El Backlog Recovery tradujo dicho conocimiento en historias de usuario trazables al código.

En conjunto, estas tareas proporcionan una comprensión sólida y verificable del sistema, necesaria para avanzar hacia actividades de gobernanza, auditoría de deuda técnica y hardening en entregas posteriores.
