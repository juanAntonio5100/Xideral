
IF NOT EXISTS (SELECT NAME FROM SYS.databases WHERE NAME = 'XIDERALPRUEBA_DB')
BEGIN
	CREATE DATABASE XIDERALPRUEBA_DB
	PRINT 'SE CREA BASE DE DATOS...'
END
ELSE
	PRINT 'BASE DE DATOS YA ESTA CREADA...'
GO

USE XIDERALPRUEBA_DB
GO

CREATE TABLE Usuarios
(
	Usuario_ID INT IDENTITY(1,1),
	Usuario_Alias VARCHAR(45),
	Usuario_Password VARCHAR(45),
	Usuario_Rol VARCHAR(45),
)
GO

ALTER TABLE Usuarios ADD CONSTRAINT PK_USUARIO PRIMARY KEY (Usuario_ID)
GO

CREATE TABLE Tareas
(
Tarea_ID INT IDENTITY(1,1),
Tarea_Titulo VARCHAR(45),
Tarea_Descripcion VARCHAR(45),
Tarea_Fecha_Vencimiento DATETIME,
Usuario_ID INT NULL
)
GO

ALTER TABLE Tareas ADD CONSTRAINT PK_TAREA PRIMARY KEY (Tarea_ID)
GO

ALTER TABLE Tareas ADD CONSTRAINT FK_USUARIO FOREIGN KEY (Usuario_ID) REFERENCES Usuarios(Usuario_ID);
GO


INSERT INTO [dbo].[Usuarios]
           ([Usuario_Alias]
           ,[Usuario_Password]
           ,[Usuario_Rol])
     VALUES
           ('jmartinez',
		   '1234',
		   'ADMINISTRADOR'
		   )
GO
