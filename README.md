# Proyecto-de-progra-2
CREATE TABLE Equipos (
    id_equipo INT PRIMARY KEY,
    nombre_equipo VARCHAR(50),
    descripcion TEXT
);

CREATE TABLE Usuarios (
    id_usuario INT PRIMARY KEY,
    nombre_usuario VARCHAR(50),
    email VARCHAR(50)
);

CREATE TABLE Tecnicos (
    id_tecnico INT PRIMARY KEY,
    nombre_tecnico VARCHAR(50),
    especialidad VARCHAR(50)
);

CREATE TABLE Mantenimiento (
    id_mantenimiento INT PRIMARY KEY,
    id_equipo INT,
    id_usuario INT,
    id_tecnico INT,
    fecha DATE,
    FOREIGN KEY (id_equipo) REFERENCES Equipos(id_equipo),
    FOREIGN KEY (id_usuario) REFERENCES Usuarios(id_usuario),
    FOREIGN KEY (id_tecnico) REFERENCES Tecnicos(id_tecnico)
);
//2. Mantenimiento de tablas (CRUD)

//Agregar
INSERT INTO Equipos (id_equipo, nombre_equipo, descripcion) VALUES (1, 'Equipo A', 'Descripción del equipo A');
INSERT INTO Usuarios (id_usuario, nombre_usuario, email) VALUES (1, 'Usuario A', 'usuarioA@example.com');
INSERT INTO Tecnicos (id_tecnico, nombre_tecnico, especialidad) VALUES (1, 'Tecnico A', 'Especialidad A');
Borrar
DELETE FROM Equipos WHERE id_equipo = 1;
DELETE FROM Usuarios WHERE id_usuario = 1;
DELETE FROM Tecnicos WHERE id_tecnico = 1;
//Consultar
SELECT * FROM Equipos;
SELECT * FROM Usuarios;
SELECT * FROM Tecnicos;
//Modificar
UPDATE Equipos SET nombre_equipo = 'Equipo B' WHERE id_equipo = 1;
UPDATE Usuarios SET nombre_usuario = 'Usuario B' WHERE id_usuario = 1;
UPDATE Tecnicos SET nombre_tecnico = 'Tecnico B' WHERE id_tecnico = 1;
//3. Procedimientos almacenados
//Crear
CREATE PROCEDURE agregarEquipo(IN id INT, IN nombre VARCHAR(50), IN descripcion TEXT)
BEGIN
    INSERT INTO Equipos (id_equipo, nombre_equipo, descripcion) VALUES (id, nombre, descripcion);
END;
//Borrar
CREATE PROCEDURE borrarEquipo(IN id INT)
BEGIN
    DELETE FROM Equipos WHERE id_equipo = id;
END;
//Consultar
CREATE PROCEDURE consultarEquipos()
BEGIN
    SELECT * FROM Equipos;
END;
//Modificar
CREATE PROCEDURE modificarEquipo(IN id INT, IN nombre VARCHAR(50))
BEGIN
    UPDATE Equipos SET nombre_equipo = nombre WHERE id_equipo = id;
END;
//4. Sistema con capas de Modelo, Vistas y Lógica
//Modelo (PHP)
class Equipo {
    public $id_equipo;
    public $nombre_equipo;
    public $descripcion;

    // Métodos para CRUD
}
//Vista (HTML y CSS)
<!DOCTYPE html>
<html>
<head>
    <title>Equipos</title>
    <style>
        /* Estilos CSS */
    </style>
</head>
<body>
    <h1>Lista de Equipos</h1>
    <!-- Código HTML para mostrar equipos -->
</body>
</html>
//Lógica (PHP)
include 'modelo.php';

function mostrarEquipos() {
    // Código para consultar y mostrar equipos
}
//5. Ventana de Login
<!DOCTYPE html>
<html>
<head>
    <title>Login</title>
</head>
<body>
    <form action="login.php" method="post">
        <label for="username">Usuario:</label>
        <input type="text" id="username" name="username">
        <label for="password">Contraseña:</label>
        <input type="password" id="password" name="password">
        <button type="submit">Login</button>
    </form>
</body>
</html>
