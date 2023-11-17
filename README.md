# Desarrollo Web en Entorno Servidor (DSW)
---
### Integrantes:
#### - Richard Francisco Vaca Garcia
#### - Amin Housnane León
#### - Airam de León Perera
---
### Proyecto Grupal 1: ChampionCraft

ChampionCraft es una innovadora plataforma online dedicada a la creación y gestión de personajes personalizados de League of Legends. Esta página permite a los usuarios diseñar personajes con detalles únicos como nombre, rol, procedencia, recurso, tipo de golpe e imagen, guardándolos en un entorno virtual.

### Servicios Ofrecidos:
1. **Creación de Personajes Personalizados:**
   - Diseño detallado de personajes con opciones de personalización en nombre, rol, procedencia, etc.
   - Posibilidad de guardar y gestionar hasta 10 personajes gratuitamente.

2. **Suscripción Premium:**
   - Por €6,99 al mes, los usuarios tienen capacidad ilimitada de creación y almacenamiento de personajes.
   - Los personajes no se borrarán automáticamente y podrán exportarse en varios formatos.
   - Acceso a expertos en League of Legends para asesoramiento personalizado.

### Requisitos de la Página Web:
1. **Interfaz de Usuario:**
   - Diseño interactivo y atractivo, temáticamente alineado con League of Legends.
   - Facilidad de uso con un sistema de creación de personajes intuitivo.

2. **Funcionalidades:**
   - Herramientas de personalización de personajes con vista previa en tiempo real.
   - Sistema de gestión de personajes con opciones de edición y borrado.
   - Mecanismo de suscripción y pago seguro para la versión premium.

3. **Seguridad:**
   - Protección de datos personales y transacciones seguras.
   - Cumplimiento con las normativas de seguridad y privacidad en línea.

4. **Soporte al Cliente:**
   - Chat en vivo y soporte técnico para usuarios premium.
   - Sección de FAQ y guías de uso.

5. **Gestión de Contenidos:**
   - Panel de administración para la gestión de suscripciones y asesoramientos.
   - Actualizaciones periódicas con nuevas características y mejoras.

6. **SEO y Marketing:**
   - Estrategias SEO para una mayor visibilidad en buscadores.
   - Campañas promocionales en redes sociales y plataformas relacionadas con gaming.

7. **Accesibilidad:**
   - Diseño accesible y compatible con distintos navegadores y dispositivos.

---

### Casos de Uso:
1. **Usuario Regular:**
   - **Creación y Gestión de Personajes:**
      - Crear, editar y borrar hasta 10 personajes.
   - **Exportación de Personajes:**
      - Exportar personajes en formatos estándar (solo usuarios premium).

2. **Usuario Premium:**
   - **Creación y Gestión Ilimitada de Personajes:**
      - Sin límite en la cantidad y permanencia de personajes.
   - **Acceso a Asesoramiento Experto:**
      - Consultas y consejos de expertos en League of Legends.

### Base de Datos en PHP:

```sql
CREATE TABLE Usuarios (
    UsuarioID INT AUTO_INCREMENT PRIMARY KEY,
    NombreUsuario VARCHAR(255),
    Contrasena VARCHAR(255),
    Correo VARCHAR(255),
    TipoUsuario ENUM('Regular', 'Premium')
);

CREATE TABLE Personajes (
    PersonajeID INT AUTO_INCREMENT PRIMARY KEY,
    UsuarioID INT,
    Nombre VARCHAR(255),
    Rol VARCHAR(255),
    Procedencia VARCHAR(255),
    Recurso VARCHAR(255),
    TipoGolpe VARCHAR(255),
    Imagen VARCHAR(255),
    FOREIGN KEY (UsuarioID) REFERENCES Usuarios(UsuarioID)
);

CREATE TABLE Suscripciones (
    SuscripcionID INT AUTO_INCREMENT PRIMARY KEY,
    UsuarioID INT,
    FechaInicio DATE,
    FechaFin DATE,
    FOREIGN KEY (UsuarioID) REFERENCES Usuarios(UsuarioID)
);
```

### Conexión a la Base de Datos con PHP:

```php
<?php
$nombreServidor = "ChampionCraftDB";
$nombreUsuario = "UserCraft";
$contrasena = "Craft1234";
$nombreBaseDatos = "BD_ChampionCraft";

// Crear conexión
$conn = new mysqli($nombreServidor, $nombreUsuario, $contras

ena, $nombreBaseDatos);

// Verificar conexión
if ($conn->connect_error) {
    die("La conexión ha fallado: " . $conn->connect_error);
}
?>
```

---

### Entidades y Atributos

1. **Usuario**
   - **Atributos:** UsuarioID (clave primaria), NombreUsuario, Contraseña, Correo, TipoUsuario (Regular, Premium)

2. **Personaje**
   - **Atributos:** PersonajeID (clave primaria), UsuarioID (clave foránea), Nombre, Rol, Procedencia, Recurso, TipoGolpe, Imagen

3. **Suscripción**
   - **Atributos:** SuscripcionID (clave primaria), UsuarioID (clave foránea), FechaInicio, FechaFin

### Relaciones

1. **Usuario - Personaje**
   - Un usuario puede crear y gestionar varios personajes.
   - Un personaje está asociado a un solo usuario.
   - Relación: Uno a muchos (1:N)

2. **Usuario - Suscripción**
   - Un usuario puede tener una suscripción premium.
   - Una suscripción está asociada a un solo usuario.
   - Relación: Uno a uno (1:1) o uno a muchos (1:N), dependiendo de si permites múltiples suscripciones para un usuario.

### Diagrama ER

El diagrama entidad-relación se vería así:

- **Usuario**
  - UsuarioID (PK)
  - NombreUsuario
  - Contraseña
  - Correo
  - TipoUsuario

- **Personaje**
  - PersonajeID (PK)
  - UsuarioID (FK)
  - Nombre
  - Rol
  - Procedencia
  - Recurso
  - TipoGolpe
  - Imagen

- **Suscripción**
  - SuscripcionID (PK)
  - UsuarioID (FK)
  - FechaInicio
  - FechaFin

Las líneas conectan el UsuarioID en la entidad **Usuario** con el UsuarioID en **Personaje** y **Suscripción**, mostrando las relaciones. En un software de diagramación, estas líneas se dibujarían con etiquetas para indicar el tipo de relación (1:N o 1:1).

---

Este es el diagrama de entidad-relación utilizando el lenguaje mermaid. Nos falta realizarlo en el lenguaje Graphviz.

![Diagrama ER de ChampionCraft](https://i.postimg.cc/0yZhjzcs/diagram-1.jpg)


---

### Conclusión:
ChampionCraft se presenta como una plataforma única y atractiva para los aficionados de League of Legends, ofreciendo una experiencia personalizada en la creación de personajes. Con una interfaz amigable y opciones tanto gratuitas como premium, ChampionCraft busca posicionarse como una herramienta esencial para los jugadores que buscan explorar y expandir su creatividad en el universo de League of Legends.