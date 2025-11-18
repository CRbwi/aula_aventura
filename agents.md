Eres un desarrollador de software experto, especializado en la creación de aplicaciones web educativas del lado del servidor. Tu tarea es generar el código base para una plataforma web "Todo en uno" llamada "AulaAventura", utilizando PHP, HTML, CSS y MariaDB. Esta plataforma permitirá a los docentes crear y gestionar experiencias de aprendizaje gamificadas para sus estudiantes.

Existe un fichero llamado progreso.md que es lo que has implementado, cada vez que leas este fichero de PROYECTO_AULA_AVENTURA.md revisa en progreso.md lo que ya hiciste anteriormente y de lo que ves aquí abajo nuevo es lo que tienes que implementar y  saltar lo que ya has hecho.

Tecnologías a utilizar:
• Backend (Lógica del servidor): PHP 8 (orientado a objetos).
• Frontend (Estructura y estilos): HTML5 y CSS3 (puedes usar un framework como Bootstrap para acelerar el diseño responsivo).
• Base de datos: MariaDB. (tengo ya un contenedor en este servidor que puedes usar si quieres subir la base de datos)
• Interacción dinámica en el frontend (sin recargar la página): JavaScript (Vanilla JS) y AJAX para la comunicación asíncrona con el servidor PHP.
• Servidor web (para un entorno de desarrollo): Apache. (comentarte que ya estas trabajando en una carpeta en un servidor apache)

Estructura del proyecto: Genera una estructura de carpetas organizada para un proyecto PHP tradicional. Por ejemplo:
• / (raíz del proyecto)
    ◦ index.php (punto de entrada)
    ◦ config/ (para la conexión a la base de datos y otras configuraciones)
    ◦ controllers/ (lógica que maneja las peticiones de los usuarios)
    ◦ models/ (clases para interactuar con la base de datos)
    ◦ views/ (archivos HTML/PHP para la presentación, plantillas)
    ◦ assets/ (CSS, JavaScript, imágenes)

Descripción detallada de la aplicación "AulaAventura":
1. Roles de Usuario y Gestión de Sesiones:
• Docente: Puede crear "clases", invitar estudiantes, diseñar actividades ("Misiones"), asignar puntos y ver el progreso de los alumnos.
• Estudiante: Se une a una clase con un código, personaliza su avatar, participa en misiones, gana puntos (XP) y medallas, y ve su ranking.
• Padre/Tutor (Opcional): Puede ver el progreso de su hijo/a, similar a ClassDojo.
• Utiliza sesiones de PHP ($_SESSION) para gestionar la autenticación de los usuarios.

2. Módulo de Creación de Actividades (para el Docente): Esta es la funcionalidad central. El docente debe poder crear "Misiones" que son secuencias de diferentes tipos de retos, inspirados en herramientas como Genially, Cerebriti y Educaplay. Los tipos de actividades a incluir son:
• Cuestionarios Interactivos (tipo Kahoot!/Quizizz):
    ◦ Preguntas de opción múltiple, verdadero/falso.
    ◦ Posibilidad de añadir imágenes.
    ◦ Se puede jugar en vivo (usando AJAX para actualizar preguntas y respuestas) o como tarea asincrónica.
• Juegos de Tarjetas (Flashcards): Inspirado en Brainscape o Quizlet. El docente crea conjuntos de tarjetas digitales para repasar conceptos.
• "Escape Room" Digital: Inspirado en Breakout EDU. El docente crea una secuencia de acertijos (que pueden ser los cuestionarios anteriores u otros retos) que los estudiantes deben resolver para obtener una contraseña que "desbloquee" la siguiente etapa de la misión.
• Sopas de letras y Crucigramas: Inspirado en Educaplay y WorldWall.

3. Sistema de Gamificación y Progresión (para el Estudiante): La plataforma debe tener un sistema de progresión claro, inspirado en Classcraft.
• Puntos de Experiencia (XP): Se ganan al completar actividades y sirven para subir de nivel.
• Avatares y Personalización: Cada estudiante elige un avatar y puede personalizar su apariencia.
• Clases de Personajes (Guerrero, Mago, Sanador): Cada clase tiene "poderes" únicos que pueden usar en el "juego" de la clase. Por ejemplo, "Sanar" a un compañero para ayudarle a recuperar "puntos de vida" si se implementa un sistema así.
• Insignias y Logros (Badges): Recompensas visuales por alcanzar hitos (ej. "Completar 10 misiones").
• Tabla de Clasificación (Leaderboard): Muestra el ranking de estudiantes basado en XP.

4. Panel del Docente (Dashboard): El docente debe tener una vista general de su clase.
• Vista de todos los estudiantes, sus niveles y progreso.
• Generación de informes de evaluación.
• Capacidad de otorgar XP manualmente por comportamientos positivos en clase.

5. Interfaz y Experiencia de Usuario (UX):
• La interfaz debe ser visualmente atractiva, intuitiva y fácil de usar.
• Debe ser "responsive" y funcionar en ordenadores, tabletas y móviles. Se recomienda usar Bootstrap para facilitar el diseño.
Instrucción Inicial: Comienza generando el esquema de la base de datos en SQL para MariaDB. Crea las tablas necesarias con sus relaciones:
1. usuarios (con campos para id, nombre, email, hash_contraseña, rol).
2. clases (con campos para id, nombre_clase, codigo_invitacion, id_docente).
3. usuarios_clases (tabla intermedia para la relación muchos a muchos entre usuarios y clases).
4. personajes (con campos para id_usuario, id_clase, tipo_personaje, xp, nivel, etc.).
5. misiones (id, id_clase, titulo, descripcion).
6. actividades (id, id_mision, tipo_actividad, contenido_json).
7. respuestas_actividades (id, id_actividad, id_usuario, respuesta, es_correcta, etc.).
A continuación, genera el código PHP inicial:
1. config/database.php: Un script que gestione la conexión a la base de datos MariaDB usando PDO o MySQLi.
2. models/Usuario.php: Una clase Usuario con métodos para registrar(), login() y obtenerPorId().
3. controllers/AuthController.php: Lógica para manejar las peticiones de registro y login, interactuando con el modelo Usuario y gestionando las sesiones ($_SESSION).
4. views/login.php y views/registro.php: Formularios HTML básicos para que los usuarios puedan iniciar sesión o crear una cuenta.
