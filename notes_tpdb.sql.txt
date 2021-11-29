- Volcado de MySQL 10.13 Distrib 5.5.62, para Win64 (AMD64)
-
- Anfitrión: base de datos localhost: notes_db
- ------------------------------------------------ ------
- Versión del servidor 5.5.5-10.4.20-MariaDB

/ * ! 40101 SET @OLD_CHARACTER_SET_CLIENT = @@ CHARACTER_SET_CLIENT * / ;
/ * ! 40101 SET @OLD_CHARACTER_SET_RESULTS = @@ CHARACTER_SET_RESULTS * / ;
/ * ! 40101 SET @OLD_COLLATION_CONNECTION = @@ COLLATION_CONNECTION * / ;
/ * ! 40101 ESTABLECER NOMBRES utf8 * / ;
/ * ! 40103 SET @OLD_TIME_ZONE = @@ TIME_ZONE * / ;
/ * ! 40103 SET TIME_ZONE = '+ 00:00' * / ;
/ * ! 40014 SET @OLD_UNIQUE_CHECKS = @@ UNIQUE_CHECKS, UNIQUE_CHECKS = 0 * / ;
/ * ! 40014 SET @OLD_FOREIGN_KEY_CHECKS = @@ FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS = 0 * / ;
/ * ! 40101 SET @OLD_SQL_MODE = @@ SQL_MODE, SQL_MODE = 'NO_AUTO_VALUE_ON_ZERO' * / ;
/ * ! 40111 SET @OLD_SQL_NOTES = @@ SQL_NOTES, SQL_NOTES = 0 * / ;

-
- Estructura de la tabla para las `categorías` de la tabla
-

DROP  TABLE SI EXISTE " categorías " ;
/ * ! 40101 SET @saved_cs_client = @@ character_set_client * / ;
/ * ! 40101 SET character_set_client = utf8 * / ;
CREAR  TABLA ` categorías` (
  ` Identificación del `  int ( 11 ) NOT NULL AUTO_INCREMENT,
  ` Nombre `  varchar ( 50 ) DEFAULT NULL ,
  PRIMARY KEY ( ` Identificación del ` ),
  UNIQUE KEY ` categories_un ` ( ` Identificación del ` , ` nombre ' )
) MOTOR = InnoDB DEFAULT CHARSET = utf8mb4;
/ * ! 40101 SET character_set_client = @saved_cs_client * / ;

-
- Volcado de datos para las `categorías` de la tabla
-

TABLAS DE BLOQUEO ` categorías ` ESCRIBIR;
/ * ! 40000 ALTER TABLE `categorías` DESHABILITAR TECLAS * / ;
/ * ! 40000 ALTER TABLE `categorías` HABILITAR TECLAS * / ;
DESBLOQUEAR TABLAS;

-
- Estructura de la tabla para la tabla `deteled_notes`
-

DROP  TABLE IF EXISTS ` deteled_notes ` ;
/ * ! 40101 SET @saved_cs_client = @@ character_set_client * / ;
/ * ! 40101 SET character_set_client = utf8 * / ;
CREAR  TABLA ` deteled_notes` (
  ` Identificación del `  int ( 11 ) NOT NULL AUTO_INCREMENT,
  ` User_id `  int ( 11 ) NOT NULL ,
  ` Note_id `  int ( 11 ) NOT NULL ,
  PRIMARY KEY ( ` Identificación del ` ),
  KEY ` deteled_notes_FK ` ( ` note_id ` ),
  KEY ` deteled_notes_FK_1 ` ( ` user_id ` ),
  CONSTRAINT  ` deteled_notes_FK `  clave externa ( ` note_id ` ) Referencias  ` notas ` ( ` Identificación del ` ),
  CONSTRAINT  ` deteled_notes_FK_1 `  FOREIGN KEY ( ` user_id ` ) Referencias  ` usuario ` ( ` Identificación del ` )
) MOTOR = InnoDB DEFAULT CHARSET = utf8mb4;
/ * ! 40101 SET character_set_client = @saved_cs_client * / ;

-
- Volcado de datos para la tabla `deteled_notes`
-

LOCK TABLES ` deteled_notes ` WRITE;
/ * ! 40000 ALTER TABLE `deteled_notes` DESHABILITAR TECLAS * / ;
/ * ! 40000 ALTER TABLE `deteled_notes` HABILITAR TECLAS * / ;
DESBLOQUEAR TABLAS;

-
- Estructura de la tabla para la tabla `notes`
-

DROP  TABLE IF EXISTS ` notas ` ;
/ * ! 40101 SET @saved_cs_client = @@ character_set_client * / ;
/ * ! 40101 SET character_set_client = utf8 * / ;
CREATE  TABLE ` notas ` (
  ` Identificación del `  int ( 11 ) NOT NULL AUTO_INCREMENT,
  ` Título `  varchar ( 100 ) NOT NULL ,
  ` Created_at `  fecha  NOT NULL ,
  ` Updated_at `  fecha DEFAULT NULL ,
  ` Security_level ` binario ( 1 ) NOT NULL ,
  ` User_id `  int ( 11 ) NOT NULL ,
  ` Contenido '  texto  NOT NULL ,
  ` Is_active ` binario ( 1 ) NOT NULL ,
  PRIMARY KEY ( ` Identificación del ` ),
  UNIQUE KEY ` notes_un ` ( ` Identificación del ` ),
  KEY ` notes_FK ` ( ` user_id ` ),
  CONSTRAINT  ` notes_FK `  FOREIGN KEY ( ` user_id ` ) Referencias  ` usuario ` ( ` Identificación del ` )
) MOTOR = InnoDB DEFAULT CHARSET = utf8mb4;
/ * ! 40101 SET character_set_client = @saved_cs_client * / ;

-
- Volcado de datos para la tabla `notes`
-

LOCK TABLES ` notas ` WRITE;
/ * ! 40000 ALTER TABLE `notas` DESHABILITAR TECLAS * / ;
/ * ! 40000 ALTER TABLE `notas` HABILITAR TECLAS * / ;
DESBLOQUEAR TABLAS;

-
- Estructura de la tabla para la tabla `notes_categories`
-

DROP  TABLE IF EXISTS ` notes_categories ` ;
/ * ! 40101 SET @saved_cs_client = @@ character_set_client * / ;
/ * ! 40101 SET character_set_client = utf8 * / ;
CREAR  TABLA ` notes_categories` (
  ` Identificación del `  int ( 11 ) NOT NULL AUTO_INCREMENT,
  ` Category_id `  int ( 11 ) NOT NULL ,
  ` Note_id `  int ( 11 ) NOT NULL ,
  PRIMARY KEY ( ` Identificación del ` ),
  UNIQUE KEY ` notes_categories_un ` ( ` Identificación del ` ),
  KEY ` notes_categories_FK ` ( ` category_id ` ),
  KEY ` notes_categories_FK_1 ` ( ` note_id ` ),
  RESTRICCIÓN  ` notes_categories_FK `  FOREIGN KEY ( ` category_id ` ) REFERENCIAS  ` categorías ` ( ` Identificación del ` ),
  CONSTRAINT  ` notes_categories_FK_1 `  FOREIGN KEY ( ` note_id ` ) Referencias  ` notas ` ( ` Identificación del ` )
) MOTOR = InnoDB DEFAULT CHARSET = utf8mb4;
/ * ! 40101 SET character_set_client = @saved_cs_client * / ;

-
- Volcado de datos para la tabla `notes_categories`
-

LOCK TABLES ` notes_categories ` WRITE;
/ * ! 40000 ALTER TABLE `notes_categories` DESHABILITAR TECLAS * / ;
/ * ! 40000 ALTER TABLE `notes_categories` HABILITAR TECLAS * / ;
DESBLOQUEAR TABLAS;

-
- Estructura de la tabla para la tabla `usuario`
-

DROP  TABLE SI EXISTE ' usuario ' ;
/ * ! 40101 SET @saved_cs_client = @@ character_set_client * / ;
/ * ! 40101 SET character_set_client = utf8 * / ;
CREATE  TABLE ` usuario ` (
  ` Identificación del `  int ( 11 ) NOT NULL AUTO_INCREMENT,
  ` Nombre de `  varchar ( 100 ) NOT NULL ,
  ` Email `  varchar ( 100 ) NOT NULL ,
  PRIMARY KEY ( ` Identificación del ` ),
  UNIQUE KEY ` user_un ` ( ` correo electrónico ' , ` Identificación del ` )
) MOTOR = InnoDB DEFAULT CHARSET = utf8mb4;
/ * ! 40101 SET character_set_client = @saved_cs_client * / ;

-
- Volcado de datos para la tabla `usuario`
-

LOCK TABLES ` usuario ` WRITE;
/ * ! 40000 ALTER TABLE `usuario` DESHABILITAR TECLAS * / ;
/ * ! 40000 ALTER TABLE `usuario` ENABLE KEYS * / ;
DESBLOQUEAR TABLAS;

-
- Rutinas de volcado para la base de datos 'notes_db'
-
/ * ! 40103 SET TIME_ZONE = @ OLD_TIME_ZONE * / ;

/ * ! 40101 SET SQL_MODE = @ OLD_SQL_MODE * / ;
/ * ! 40014 SET FOREIGN_KEY_CHECKS = @ OLD_FOREIGN_KEY_CHECKS * / ;
/ * ! 40014 SET UNIQUE_CHECKS = @ OLD_UNIQUE_CHECKS * / ;
/ * ! 40101 SET CHARACTER_SET_CLIENT = @ OLD_CHARACTER_SET_CLIENT * / ;
/ * ! 40101 SET CHARACTER_SET_RESULTS = @ OLD_CHARACTER_SET_RESULTS * / ;
/ * ! 40101 SET COLLATION_CONNECTION = @ OLD_COLLATION_CONNECTION * / ;
/ * ! 40111 SET SQL_NOTES = @ OLD_SQL_NOTES * / ;

- Volcado completado el 2021-09-23 11:19:39