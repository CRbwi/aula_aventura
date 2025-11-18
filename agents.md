# 📝 PROYECTO\_AULA\_AVENTURA: Plan Maestro

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
| **Fase 3** | **Motor de Misiones y Progresión Básica** | CRUD de Misiones. Creación del primer tipo de actividad (**Cuestionario**). Sistema de **XP, Nivelación y Leaderboard** (solo XP). | **Verificar:** Docente asigna Quiz. Estudiante lo completa y gana XP. | Pendiente |
| **Fase 4** | **Gamificación Avanzada y Moneda** | Implementación de la **Moneda Virtual ("Gemmas")**. Creación del módulo **Flashcards**. Panel de Tutor (solo vista). | **Verificar:** Estudiante gana Gemmas con XP. Docente ve el progreso del Tutor. | Pendiente |
| **Fase 5+** | **Módulos Complejos y Tienda** | **Escape Room** (Desbloqueo secuencial). **Sopas/Crucigramas**. Implementación de **Tienda** y uso de **Poderes de Personaje**. | (Definido en fases futuras) | Pendiente |

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

### 1. 🎮 Sistema de Gamificación y Progresión (Mejorado - Tendencias Actuales)

El sistema debe ser moderno y fomentar la retención y la participación social.

* **Puntos de Experiencia (XP) y Niveles:** Se ganan al completar actividades. La nivelación debe seguir una curva de dificultad creciente ($XP_{requerido} = 100 \times Nivel^2$).
* **Moneda Virtual:** Implementación de **"Gemmas"** o **"Créditos de Aventura"**.
    * **Obtención:** Se ganan con XP o recompensas por rachas.
    * **Uso:** Se gastan en la **"Tienda de Ítems"** para comprar elementos cosméticos de avatar y **Ventajas** temporales (ej. un *doble de XP* por una misión).
* **Clases y Poderes (Héroe-Base):**
    * **Clases:** Guerrero, Mago, Sanador.
    * **Poderes Activos:** Cada clase tendrá 2-3 habilidades que pueden usarse **una vez por sesión de clase** o con un **tiempo de recarga (Cooldown)**, forzando la estrategia de equipo.
* **Rachas de Actividad (Streaks):** Recompensa con XP y Gemmas por mantener una racha de días consecutivos de actividad, promoviendo el hábito.
* **Insignias y Logros (Badges):** Recompensas visuales por hitos (ej. "Maestro de Flashcards").
* **Tabla de Clasificación (Leaderboard):** Ranking de estudiantes por XP. Deberá incluir **filtros** por clase y por período (semanal/total).

### 2. Módulo de Creación de Actividades

El docente debe tener un *suite* de herramientas variado:

* **Cuestionarios Interactivos (Kahoot!/Quizizz):** Preguntas de opción múltiple, V/F. **Soporte multimedia** y opción de modo **En Vivo (AJAX)**.
* **Juegos de Tarjetas (Flashcards):** Repaso con *Spaced Repetition* (modelo simplificado para optimizar la retención).
* **"Escape Room" Digital (Breakout EDU):** Secuencia lineal de actividades, donde la respuesta correcta a un acertijo genera la **contraseña** que desbloquea la siguiente etapa.
* **Sopas de letras y Crucigramas (Educaplay):** Creación basada en listas de vocabulario.
* **Tareas de Subida/Entrega:** Permitir al docente asignar trabajos que requieran la subida de un archivo o texto para revisión manual.

### 3. Panel del Docente (Dashboard)

El centro de mando para la gestión de la clase.

* **Vista de Progreso:** Nivel, XP, Gemmas y Clase de Personaje de cada estudiante.
* **Informes y Analíticas:** Generación de informes de rendimiento por Misión y por alumno.
* **Gestión de Refuerzo:** Capacidad de otorgar **XP y Gemmas manualmente** por comportamiento positivo o participación.
* **Herramientas de Clase:** Generación y gestión del código de invitación de clase.

---

## 🚧 Tarea de la Fase 1: Implementación Inicial

**Instrucción:** Genera el esquema de la base de datos y el código PHP para el módulo de autenticación.

### 1. Esquema de Base de Datos (SQL para MariaDB)

Genera el SQL completo para crear las siguientes tablas, asegurando las claves foráneas:

* `usuarios`
* `clases`
* `usuarios_clases`
* `personajes` (Debe incluir `monedas_virtuales`, `xp`, `nivel`, `tipo_personaje`).
* `misiones`
* `actividades` (Usando `contenido_json` para almacenar la estructura de los retos).
* `respuestas_actividades`
* `insignias` y `usuarios_insignias`

### 2. Código Base Inicial (PHP)

Genera los archivos principales:

* `config/database.php`: Script de conexión PDO seguro.
* `models/Usuario.php`: Clase `Usuario` con métodos `registrar()`, `login()`, `obtenerPorId()`.
* `controllers/AuthController.php`: Lógica para manejar peticiones de `login`, `registro` y `logout`, gestionando las sesiones (`$_SESSION`).
* `views/login.php` y `views/registro.php`: Vistas de formularios HTML (usando Bootstrap).

**FIN DE LA FASE 1.** Una vez implementado este código y verificado su funcionamiento, actualiza `progreso.md` y espera la siguiente instrucción para pasar a la Fase 2.