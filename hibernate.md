**Hibernate** es un framework de mapeo objeto-relacional (ORM) que facilita el trabajo con bases de datos desde Java. Te permite abstraer la complejidad de las consultas SQL y trabajar con objetos Java.

**Conceptos clave de Hibernate:**

- Entidades: Clases Java que representan entidades en la base de datos.
- Mapeo: El proceso de asociar entidades Java con tablas de la base de datos.
- Sesiones: Objetos que representan una unidad de trabajo con la base de datos.
- Consultas HQL: Un lenguaje de consulta similar a SQL que se utiliza para recuperar entidades de la base de datos.

**Ejemplo de conexión a Hibernate:**

```Java
Configuration configuration = new Configuration();
configuration.configure("hibernate.cfg.xml");

SessionFactory sessionFactory = configuration.buildSessionFactory();
Session session = sessionFactory.openSession();
```

**Ejemplo de CRUD con Hibernate:**

Crear:

```Java
User user = new User();
user.setName("John Doe");
user.setEmail("john.doe@example.com");

session.save(user);
```

Leer:

```Java
User user = session.get(User.class, 1);

System.out.println(user.getName());
```

Actualizar:

```Java
User user = session.get(User.class, 1);
user.setName("Jane Doe");

session.update(user);
```

Eliminar:

```Java
User user = session.get(User.class, 1);

session.delete(user);
```

**Relación con JDBC:**

Hibernate utiliza JDBC internamente para realizar operaciones en la base de datos. Sin embargo, te abstrae de la complejidad de JDBC y te permite trabajar con objetos Java en lugar de consultas SQL.

**Uso con Maven:**

Hibernate se puede usar con Maven para gestionar las dependencias del proyecto y la configuración de Hibernate.

Ejemplo de configuración de Hibernate con Maven:

```
XML
<dependency>
  <groupId>org.hibernate</groupId>
  <artifactId>hibernate-core</artifactId>
  <version>5.6.10.Final</version>
</dependency>
```

**Resumen:**

- Hibernate es un framework ORM que facilita el trabajo con bases de datos desde Java.
- Te permite abstraer la complejidad de las consultas SQL y trabajar con objetos Java.
- Se puede usar con o sin Maven.
