# java-db-connections

### Principales formas de conexión en Java:

**1-JDBC (Java Database Connectivity):**

JDBC es una API estándar de Java que proporciona métodos para conectarse a una base de datos, enviar consultas SQL y procesar los resultados.
Se utiliza para conectarse a bases de datos relacionales como MySQL, PostgreSQL, Oracle, etc.
Puedes usar drivers JDBC proporcionados por los fabricantes de bases de datos o drivers JDBC universales:
MySQL: com.mysql.jdbc.Driver
PostgreSQL: org.postgresql.Driver

**2- JPA (Java Persistence API):**

JPA es una especificación de Java que proporciona un estándar para el mapeo objeto-relacional (ORM).
Permite a los desarrolladores trabajar con bases de datos relacionales utilizando objetos Java en lugar de consultas SQL.
**Hibernate**, EclipseLink y otros frameworks ORM **implementan la especificación JPA**.

**3-JNDI (Java Naming and Directory Interface):**

JNDI es una API que permite a las aplicaciones Java descubrir y buscar servicios de directorio y objetos Java a través de un nombre.
Se utiliza comúnmente para acceder a recursos como conexiones de bases de datos, objetos remotos, colas de mensajes, etc.

**4-Conexiones HTTP:**

Java proporciona clases como HttpURLConnection y HttpClient para realizar conexiones HTTP a servidores web.
Estas conexiones son útiles para integrar servicios web RESTful, consumir APIs de terceros, etc.

**5-Socket Programming:**

Java proporciona clases como Socket y ServerSocket para comunicación de red a un nivel más bajo.
Con Socket Programming, puedes establecer conexiones TCP/IP y UDP entre aplicaciones cliente-servidor.

**6-RMI (Remote Method Invocation):**

RMI es una API que facilita la invocación de métodos de objetos que residen en sistemas remotos.
Se utiliza para la comunicación entre procesos en Java, permitiendo que los objetos Java en diferentes JVMs se comuniquen entre sí.

**7-JMS (Java Message Service):**

JMS es una API para la creación, envío, recepción y lectura de mensajes entre aplicaciones Java.
Es útil para la implementación de sistemas de mensajería asíncrona y la integración de sistemas distribuidos.
