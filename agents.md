# 📝 PROYECTO\_AULA\_AVENTURA: Plan Maestro (v2.1 - Gamificación Avanzada)

## 🎯 Perfil del Agente

Eres un **Desarrollador de Software Experto** (Full Stack, con enfoque en Back-end), especializado en la creación de **aplicaciones web educativas del lado del servidor** (LEMS - Learning Management Systems).

Tu tarea es generar el código base y la estructura de la plataforma "**AulaAventura**", implementando soluciones seguras, escalables y orientadas a objetos.

## ⚙️ Tecnologías y Entorno

* **Backend (Lógica del servidor):** **PHP 8** (Orientado a Objetos, siguiendo el patrón MVC).
* **Frontend (Estructura y estilos):** HTML5 y CSS3. **Framework:** **Bootstrap 5** para un diseño responsive y rápido.
* **Base de Datos:** **MariaDB** (Usando un contenedor existente).
* **Interacción Dinámica:** **JavaScript (Vanilla JS)** y **AJAX** para la comunicación asíncrona.
* **Entorno de Desarrollo:** Servidor **Apache** (Carpeta de trabajo preestablecida).

---

## 🛡️ Flujo de Trabajo: Desarrollo Incremental por Fases

El proyecto seguirá un flujo de trabajo riguroso por fases, análogo a un proceso de *staging*, donde la implementación se detiene hasta que la fase actual sea revisada y validada. El archivo **`progreso.md`** es tu **Registro de Implementación** y la única fuente de verdad sobre lo que ya está hecho.

| Fase | Foco Principal | Módulos a Implementar | Testing y Verificación | Estado |
| :--- | :--- | :--- | :--- | :--- |
| **Fase 1** | **Infraestructura y Acceso Público** | Esquema DB, Conexión DB, Modelos de Usuario, **Login/Registro** (Auth). | **Verificar:** Creación de usuarios de distintos roles. Login/Logout seguro con sesiones. | **Activa** |
| **Fase 2** | **Gestión de Entidades Base** | Creación de Clases (Docente), Unión a Clases (Estudiante), **Creación de Personaje/Avatar**. | **Verificar:** Docente puede crear, Estudiante puede unirse. Personaje de Estudiante creado en DB. | Pendiente |
| **Fase 3** | **Motor de Progresión y Cuestionarios** | CRUD de Misiones. Creación del primer tipo de actividad (**Cuestionario**). Sistema de **XP, Nivelación, y el sistema de HP BÁSICO**. | **Verificar:** Estudiante gana XP/pierde HP. Leaderboard de XP funciona. | Pendiente |
| **Fase 4** | **Gamificación Avanzada y Moneda** | Implementación de la **Moneda Virtual ("Gemmas")**. Módulo **Flashcards y Micro-Misiones Diarias**. Panel de Tutor (solo vista). | **Verificar:** Estudiante gana Gemmas. Misiones diarias rotan correctamente. | Pendiente |
| **Fase 5+** | **Narrativa, Poderes y Tienda** | **Narrativa de Elección Múltiple** (sustituye Escape Room). Implementación de **Tienda**, **Cajas de Botín** y uso de **Poderes de Personaje** (usando HP). | (Definido en fases futuras) | Pendiente |

---

## 💻 Estructura del Proyecto

Se requiere la siguiente estructura de carpetas (Arquitectura **Modelo-Vista-Controlador**):

* `/` (raíz del proyecto)
    * `index.php` (Punto de entrada/Router)
    * `config/` (Conexión a la DB, Constantes)
    * `controllers/` (Lógica de negocio: `AuthController.php`, `ClaseController.php`, etc.)
    * `models/` (Clases de interacción con la DB: `Usuario.php`, `Clase.php`, etc.)
    * `views/` (Archivos de presentación: `login.php`, `docente/dashboard.php`, etc.)
    * `assets/` (Archivos estáticos: `css/`, `js/`, `img/`)

---

## ✨ Descripción Detallada de "AulaAventura"

### 1. 🎮 Sistema de Gamificación y Progresión (Reforzado con HP)

El sistema debe ser moderno y fomentar la retención y la participación social.

* **Puntos de Experiencia (XP) y Niveles:** Se ganan al completar actividades. Curva de nivelación: $XP_{requerido} = 100 \times Nivel^2$.
* **Puntos de Vida (HP):** **Nuevo Módulo Fundamental**. Cada personaje tiene HP (ej. 100%). Se pierden por errores académicos o comportamientos negativos. Se recuperan con ítems o poderes del Sanador.
* **Moneda Virtual ("Gemmas"):** Se obtienen por XP, rachas, o Micro-Misiones. Se usan en la **"Tienda de Ítems"** (cosméticos/ventajas).
* **Clases y Poderes:**
    * **Poderes Activos:** Habilidades que usan HP o Gemmas para su activación, con un **Cooldown**. El Sanador puede recuperar HP a un compañero.
* **Micro-Misiones Diarias y Cajas de Botín:** Objetivos pequeños y constantes (Rachas) con recompensas aleatorias (Cajas) para aumentar el *engagement*.
* **Insignias y Logros (Badges):** Recompensas visuales por hitos.
* **Tabla de Clasificación (Leaderboard):** Ranking de estudiantes por XP/Nivel, con filtros por clase y período.

### 2. Módulo de Creación de Actividades

El enfoque es la variedad y la baja complejidad técnica inicial.

* **Cuestionarios Interactivos (Kahoot!/Quizizz):** Preguntas de opción múltiple, V/F. **Soporte multimedia**. El fallo resta HP.
* **Juegos de Tarjetas (Flashcards):** Repaso con *Spaced Repetition* (modelo simplificado). Es el *target* principal de las Micro-Misiones.
* **Narrativa de Elección Múltiple (Sustituto de Escape Room):** El docente crea una secuencia de contenido donde el avance se basa en la **elección** del estudiante (ej. "Opción A te lleva al punto B de la Misión"). La elección incorrecta puede restar HP o XP.
* **Tareas de Subida/Entrega:** Permite la revisión manual de trabajos (para Docente).

### 3. Panel del Docente (Dashboard)

El centro de mando para la gestión de la clase.

* **Vista de Progreso:** Nivel, XP, **HP**, Gemmas y Clase de Personaje de cada estudiante.
* **Informes y Analíticas:** Generación de informes de rendimiento por Misión y por alumno.
* **Gestión de Refuerzo:** Capacidad de otorgar/restar **HP, XP y Gemmas manualmente**.
* **Herramientas de Clase:** Generación y gestión del código de invitación de clase.

---

## 🚧 Tarea de la Fase 1: Implementación Inicial

**Instrucción:** Genera el esquema de la base de datos y el código PHP para el módulo de autenticación.

### 1. Esquema de Base de Datos (SQL para MariaDB)

Genera el SQL completo para crear las siguientes tablas, asegurando las claves foráneas:

* `usuarios`
* `clases`
* `usuarios_clases`
* `personajes` (Debe incluir **`hp`**, `monedas_virtuales`, `xp`, `nivel`, `tipo_personaje`).
* `misiones`
* `actividades`
* `respuestas_actividades`
* `insignias` y `usuarios_insignias`

### 2. Código Base Inicial (PHP)

Genera los archivos principales:

* `config/database.php`: Script de conexión PDO seguro.
* `models/Usuario.php`: Clase `Usuario` con métodos `registrar()`, `login()`, `obtenerPorId()`.
* `controllers/AuthController.php`: Lógica para manejar peticiones de `login`, `registro` y `logout`, gestionando las sesiones (`$_SESSION`).
* `views/login.php` y `views/registro.php`: Vistas de formularios HTML (usando Bootstrap).

**FIN DE LA FASE 1.** Una vez implementado este código y verificado su funcionamiento, actualiza `progreso.md` y espera la siguiente instrucción para pasar a la Fase 2.