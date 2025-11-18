# 📝 PROYECTO\_AULA\_AVENTURA: Plan Maestro (v2.1 - Gamificación Avanzada)

## 🎯 Perfil del Agente

Eres un **Desarrollador de Software Experto** (Full Stack, con enfoque en Back-end), especializado en la creación de **aplicaciones web educativas del lado del servidor** (LEMS - Learning Management Systems).

Tu tarea es generar el código base y la estructura de la plataforma "**AulaAventura**", implementando soluciones seguras, escalables y orientadas a objetos.

---

## 📄 Documentación y Control de Progreso

Existe un fichero llamado **`progreso.md`** que es tu **Registro de Implementación (Changelog)**. **Siempre** debes revisarlo. La implementación debe ser **incremental**, saltando lo ya completado y enfocándote solo en la tarea de la **Fase Activa**.

---

## ⚙️ Tecnologías y Entorno

* **Backend (Lógica del servidor):** **PHP 8** (Orientado a Objetos, siguiendo el patrón MVC).
* **Frontend (Estructura y estilos):** HTML5 y CSS3. **Framework:** **Bootstrap 5** para un diseño responsive y rápido.
* **Base de Datos:** **MariaDB**. (Utilizando el contenedor existente en el servidor).
* **Interacción Dinámica:** **JavaScript (Vanilla JS)** y **AJAX** para la comunicación asíncrona (sin recarga de página).
* **Servidor web:** **Apache** (Carpeta de trabajo preestablecida).

---

## 💻 Estructura del Proyecto (MVC)

Genera la estructura de carpetas PHP tradicional:

* `/` (raíz del proyecto)
    * `index.php` (Punto de entrada/Router)
    * `config/` (Conexión a la DB, Constantes)
    * `controllers/` (Lógica de negocio: `AuthController.php`, `ClaseController.php`, etc.)
    * `models/` (Clases de interacción con la DB: `Usuario.php`, `Clase.php`, etc.)
    * `views/` (Archivos de presentación: `login.php`, `docente/dashboard.php`, etc.)
    * `assets/` (Archivos estáticos: `css/`, `js/`, `img/`)

---

## 🛡️ Flujo de Trabajo: Desarrollo Incremental por Fases

El desarrollo procede por fases, verificando la estabilidad de cada etapa:

| Fase | Foco Principal | Módulos Clave | Testing y Verificación | Estado |
| :--- | :--- | :--- | :--- | :--- |
| **Fase 1** | **Infraestructura y Acceso Público** | Esquema DB, Conexión DB, Modelos de Usuario, **Login/Registro** (Auth). | **Verificar:** Creación y autenticación segura de usuarios (Docente/Estudiante). | **Activa** |
| **Fase 2** | **Gestión de Entidades Base** | Creación de Clases (Docente), Unión a Clases (Estudiante), **Creación de Personaje/Avatar**. | **Verificar:** Docente puede crear. Estudiante se une con código y crea Personaje. | Pendiente |
| **Fase 3** | **Motor de Progresión y Cuestionarios** | CRUD de Misiones. Actividad: **Cuestionario**. Sistema de **XP, Nivelación, y el sistema de HP BÁSICO**. | **Verificar:** Estudiante gana XP/pierde HP. Leaderboard de XP funciona. | Pendiente |
| **Fase 4** | **Gamificación Avanzada y Moneda** | Implementación de la **Moneda Virtual ("Gemmas")**. Módulo **Flashcards y Micro-Misiones Diarias**. Panel de Tutor (solo vista). | **Verificar:** Estudiante gana Gemmas. Misiones diarias rotan correctamente. | Pendiente |
| **Fase 5+** | **Narrativa, Poderes y Tienda** | **Narrativa de Elección Múltiple** (sustituye Escape Room). Implementación de **Tienda**, **Cajas de Botín** y uso de **Poderes de Personaje** (usando HP). | (Definido en fases futuras) | Pendiente |

---

## ✨ Descripción Detallada de la Aplicación "AulaAventura"

### 1. Roles de Usuario y Gestión de Sesiones

* **Docente:** Crea Clases, Misiones, asigna recompensas y gestiona el progreso.
* **Estudiante:** Se une a la clase, personaliza su Personaje, participa en misiones, gana XP/Gemmas.
* **Padre/Tutor (Opcional):** Puede ver el progreso de su hijo/a (solo lectura).
* **Gestión:** Utiliza sesiones de PHP (`$_SESSION`) para la autenticación y el manejo de roles.

### 2. 🎮 Sistema de Gamificación y Progresión (Avanzado)

* **Puntos de Experiencia (XP) y Niveles:** Se ganan al completar actividades y sirven para subir de nivel.
* **Puntos de Vida (HP):** **Nuevo Módulo**. Cada personaje tiene HP (ej. 100%). Se pierden por errores académicos o comportamiento. Se recuperan con poderes o ítems.
* **Moneda Virtual ("Gemmas"):** Se obtiene por XP, rachas, o Micro-Misiones. Se usa en la **Tienda de Ítems** (cosméticos/ventajas).
* **Clases de Personajes (Guerrero, Mago, Sanador):** Cada clase tiene **Poderes Activos** (ej. "Sanar" al compañero) que tienen un **Cooldown** y se usan de forma estratégica (ligados al HP).
* **Micro-Misiones Diarias y Rachas:** Objetivos pequeños y constantes para fomentar el *engagement* diario.
* **Cajas de Botín:** Recompensas aleatorias al subir de nivel o completar misiones importantes.
* **Insignias y Logros (Badges):** Recompensas visuales por alcanzar hitos.
* **Tabla de Clasificación (Leaderboard):** Ranking de estudiantes basado en XP/Nivel, con filtros.

### 3. Módulo de Creación de Actividades

* **Cuestionarios Interactivos (Kahoot!/Quizizz):** Preguntas de opción múltiple, V/F. Soporte multimedia. Opción de juego asincrónico o en vivo (usando AJAX). El fallo resta HP.
* **Juegos de Tarjetas (Flashcards):** Conjuntos de tarjetas digitales para repaso. Utilizado en Micro-Misiones.
* **Narrativa de Elección Múltiple:** El docente crea una secuencia de contenido donde el avance se basa en la **elección** del estudiante. (Reemplaza al complejo Escape Room).
* **Sopas de letras y Crucigramas:** (Pendiente de implementación en fases avanzadas).
* **Tareas de Subida/Entrega:** Permite la revisión manual de trabajos por el Docente.

### 4. Panel del Docente (Dashboard)

* Vista de todos los estudiantes, sus niveles, **HP**, XP y Gemmas.
* Generación de informes de evaluación.
* Capacidad de otorgar/restar **HP, XP y Gemmas manualmente** por comportamientos positivos/negativos.

---

## 🚧 Tarea de la Fase 1: Implementación Inicial

**Instrucción:** Comienza generando el esquema de la base de datos y el código PHP para el módulo de autenticación.

### 1. Esquema de Base de Datos (SQL para MariaDB)

Crea las tablas necesarias con sus relaciones:

1.  `usuarios` (id, nombre, email, hash\_contraseña, rol).
2.  `clases` (id, nombre\_clase, codigo\_invitacion, id\_docente).
3.  `usuarios_clases` (tabla intermedia).
4.  `personajes` (id\_usuario, **hp**, **monedas\_virtuales**, tipo\_personaje, xp, nivel, etc.).
5.  `misiones` (id, id\_clase, titulo, descripcion).
6.  `actividades` (id, id\_mision, tipo\_actividad, contenido\_json).
7.  `respuestas_actividades` (id, id\_actividad, id\_usuario, respuesta, es\_correcta, etc.).
8.  `insignias` y `usuarios_insignias`.

### 2. Código Base Inicial (PHP)

Genera el código PHP inicial:

1.  `config/database.php`: Script que gestione la conexión a la base de datos MariaDB usando PDO.
2.  `models/Usuario.php`: Clase `Usuario` con métodos para `registrar()`, `login()` y `obtenerPorId()`.
3.  `controllers/AuthController.php`: Lógica para manejar las peticiones de registro y login, gestionando las sesiones (`$_SESSION`).
4.  `views/login.php` y `views/registro.php`: Formularios HTML básicos (usando Bootstrap).

**FIN DE LA FASE 1.**