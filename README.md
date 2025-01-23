# Trabajo Consulta 2: Conexión base de datos relacional

## ¿Qué es JDBC y cuáles son sus componentes?

JDBC (Java Database Connectivity) es una API de Java que permite a las aplicaciones Java interactuar con bases de datos relacionales de manera estándar. JDBC facilita la conexión a una base de datos, la ejecución de consultas SQL, y el manejo de los resultados de manera eficiente.


Componentes principales de JDBC:

Driver JDBC

    Es un software que actúa como puente entre la aplicación Java y la base de datos. Traducen las llamadas estándar de JDBC a instrucciones específicas para la base de datos. Existen varios tipos de controladores, como:

    Tipo 1: Bridge JDBC-ODBC
    Tipo 2: Controladores nativos-API
    Tipo 3: Protocolos de red puros
    Tipo 4: Controladores 100% Java (los más comunes hoy en día)
    
Gestor de Drivers (Driver Manager)

    Es una clase de JDBC que maneja el registro y la selección de los controladores JDBC. Su función principal es establecer una conexión entre la aplicación y la base de datos utilizando el controlador adecuado. Se utiliza el método estático DriverManager.getConnection() para obtener la conexión.


Conexión (Connection)

    Representa la conexión activa con la base de datos. A través de este objeto, la aplicación puede enviar consultas SQL y administrar transacciones. Proporciona métodos como createStatement() o prepareStatement().


Declaración (Statement)

    Se utiliza para ejecutar sentencias SQL. JDBC proporciona tres tipos principales de declaraciones:

    Statement: Para sentencias SQL simples y estáticas.
    PreparedStatement: Para consultas SQL parametrizadas y reutilizables.
    CallableStatement: Para ejecutar procedimientos almacenados en la base de datos.

    
Resultado (ResultSet)

    Es un objeto que contiene los datos devueltos por una consulta SQL. Permite navegar por los resultados fila por fila, utilizando métodos como next(), getString(), getInt(), etc.

Excepciones (SQLException)

    JDBC utiliza esta clase para manejar errores que ocurren durante la interacción con la base de datos. Proporciona métodos como getMessage(), getErrorCode(), y getSQLState() para diagnosticar problemas.


## Documente 2 librerías de Scala que permitan conectarse a una base de datos relacional. En una tabla resuma sus diferencias.

| **Librería**    | **Descripción**                                                                                      | **Ventajas**                                                                                     | **Desventajas**                                                                                 |
|------------------|----------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------|
| **Slick**       | Slick (Scala Language-Integrated Connection Kit) es una librería ORM funcional para Scala que permite trabajar con bases de datos relacionales utilizando una API basada en colecciones. Proporciona una abstracción de alto nivel para consultas SQL a través de un enfoque funcional. | - API declarativa basada en colecciones funcionales.<br>- Generación automática de consultas SQL tipadas.<br>- Buen rendimiento en operaciones comunes.<br>- Admite varios motores de bases de datos como PostgreSQL, MySQL y H2.<br>- Soporte para consultas asíncronas. | - Curva de aprendizaje empinada para principiantes.<br>- Puede ser más complejo en casos avanzados.<br>- Generación de SQL a veces difícil de depurar. |
| **Doobie**      | Doobie es una librería funcional y liviana para la interacción con bases de datos en Scala. Se basa en el ecosistema de **Cats Effect** para manejar la concurrencia y los efectos asíncronos. Es una herramienta directa que permite escribir y ejecutar SQL sin necesidad de abstracciones ORM. | - Máximo control sobre consultas SQL (se escribe SQL en bruto).<br>- Totalmente funcional y se integra bien con Cats Effect.<br>- Admite transacciones personalizadas y seguimiento de errores detallado.<br>- Ligera y sin mucha sobrecarga. | - Escribir SQL manualmente puede ser tedioso y propenso a errores.<br>- No ofrece abstracción de alto nivel como un ORM.<br>- Requiere conocimientos previos en programación funcional. |


## Documentar cómo establecer una conexión a una base de datos relacional (mysql). Siga los siguientes pasos:

### Genere una base de datos en mysql
Primero usamos la siguiente sentencia de sql en mysql:

![image](https://github.com/user-attachments/assets/4f022041-20d7-4106-bc0f-ea63ab272f6e)


### Genere una tabla con datos de prueba

![image](https://github.com/user-attachments/assets/0bb0f0f2-848b-4f23-a07f-deee7b0cb3af)

![image](https://github.com/user-attachments/assets/505b78e8-c2e9-4f18-809b-374973e3aed9)

![image](https://github.com/user-attachments/assets/0ee19c54-e775-495c-bd69-2f826ca770ab)


## Desde Scala establezca la conexión a la base datos

1. Creamos el proyecto e instalamos las dependencias:

![image](https://github.com/user-attachments/assets/24ee3169-3c28-40ba-b628-fd6c09028a29)

2.  Creamos un objeto de tipo scala en el src/main del proyecto para hacer la conexión:

![imagen_2025-01-23_150151517](https://github.com/user-attachments/assets/0767e295-e2e5-48c9-88d1-dec270df6fa9)


3. Ahora mediante un try-catch hacemos la conexión y procesamos resultados guardando en variables los datos obtenidos de la base de datos y finalmente se imprime:


![imagen_2025-01-23_151810023](https://github.com/user-attachments/assets/b4453bb0-e9e9-4eea-b6d5-722f51592189)

      





