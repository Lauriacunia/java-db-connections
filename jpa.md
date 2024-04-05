**Hibernate** es un framework de mapeo objeto-relacional (ORM) que facilita el trabajo con bases de datos desde Java. Te permite abstraer la complejidad de las consultas SQL y trabajar con objetos Java.
**Hibernate implementa la especificación JPA**.

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

Además de los métodos CRUD básicos (save, get, update, delete), el objeto Session de Hibernate también ofrece una serie de métodos importantes para trabajar con entidades y la base de datos:

**1. Métodos de carga:**

- load(Class clazz, id): Carga una entidad de la base de datos por su identificador. Si la entidad no se encuentra en la sesión, se lanza una excepción ObjectNotFoundException.
- load(Object entity, id): Similar a load(Class clazz, id), pero permite especificar la entidad a cargar.
- get(Class clazz, id): Similar a load(Class clazz, id), pero devuelve null si la entidad no se encuentra en la sesión.
- get(Object entity, id): Similar a get(Class clazz, id), pero permite especificar la entidad a cargar.

**2. Métodos de actualización:**

- update(Object entity): Actualiza el estado de una entidad en la base de datos.
- merge(Object entity): Fusiona el estado de una entidad con el estado de la entidad en la sesión. Si la entidad no se encuentra en la sesión, se inserta.
- evict(Object entity): Elimina una entidad de la sesión. La entidad no se elimina de la base de datos.

**3. Métodos de consulta:**

- createQuery(String queryString): Crea una consulta HQL.
- createSQLQuery(String queryString): Crea una consulta SQL nativa.
- createCriteria(Class clazz): Crea un objeto Criteria para realizar consultas con criterios.

**4. Métodos de transacción:**

- beginTransaction(): Inicia una transacción.
- commitTransaction(): Comete una transacción.
- rollbackTransaction(): Deshace una transacción.

**5. Métodos de cierre:**

- close(): Cierra la sesión y libera los recursos asociados.
- flush(): Sincroniza el estado de las entidades en la sesión con la base de datos.

En el contexto de Hibernate, una **sesión** representa una unidad de trabajo con la base de datos. Es un objeto que encapsula la conexión a la base de datos, las transacciones y el estado de las entidades que se están cargando o modificando.

El método flush() en la sesión se utiliza para sincronizar el estado de las entidades en la sesión con la base de datos. Esto significa que cualquier cambio realizado en las entidades en la sesión se escribe en la base de datos.

**6. Otros métodos:**

- contains(Object entity): Comprueba si una entidad está presente en la sesión.
- isDirty(Object entity): Comprueba si el estado de una entidad ha cambiado desde que se cargó en la sesión.
- refresh(Object entity): Recarga el estado de una entidad desde la base de datos.

Recuerda: Es importante cerrar la sesión cuando ya no se necesite para liberar los recursos asociados. Puedes cerrar la sesión manualmente llamando al método close() o utilizar un bloque try-with-resources para cerrar la sesión automáticamente al salir del bloque.

**¿Qué es una transacción en DB?**

En el contexto de las bases de datos, una transacción es una secuencia de operaciones que se ejecutan como una sola unidad. Todas las operaciones de la transacción deben completarse con éxito o ninguna de ellas se completará. Esto asegura que la base de datos se mantenga en un estado consistente.

Propiedades de las transacciones:

- Atomicidad: Las operaciones de la transacción deben ser atómicas, lo que significa que todas deben completarse o ninguna de ellas debe completarse.
- Consistencia: La transacción debe mantener la consistencia de la base de datos.
- Aislamiento: Las operaciones de la transacción deben estar aisladas de otras transacciones, lo que significa que no deben interferir entre sí.
- Durabilidad: Los cambios realizados por la transacción deben ser duraderos, lo que significa que no deben perderse si se produce un fallo del sistema.

Tipos de transacciones:

- Transacciones ACID: Estas transacciones cumplen con las cuatro propiedades ACID.
- Transacciones no ACID: Estas transacciones no cumplen con todas las propiedades ACID.

Ejemplo de transacción:

```Java
Session session = sessionFactory.openSession();

// Iniciar una transacción
session.beginTransaction();

// Cargar una entidad
User user = session.get(User.class, 1);

// Modificar la entidad
user.setName("John Doe");

// Guardar la entidad
session.save(user);

// Cometer la transacción
session.commitTransaction();

// Cerrar la sesión
session.close();
```
