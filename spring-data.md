**Spring Data** es un módulo de Spring Framework que facilita el acceso a datos en diferentes tipos de repositorios de información, como bases de datos relacionales, NoSQL y de búsqueda.
Spring Data proporciona una capa de abstracción sobre las API específicas de cada tipo de repositorio, lo que permite a los desarrolladores trabajar con datos de forma uniforme independientemente del tipo de repositorio que se utilice.

**Métodos importantes de Spring Data:**

**save():** Guarda una entidad en el repositorio.
**get():** Obtiene una entidad del repositorio por su identificador.
**update():** Actualiza una entidad en el repositorio.
**delete():** Elimina una entidad del repositorio.
**findAll():** Obtiene todas las entidades del repositorio.
**findByXyz():** Obtiene entidades del repositorio por un valor específico de un atributo.

**Ejemplo de conexión a una base de datos con Spring Data:**

```Java
@SpringBootApplication
public class Application {

  public static void main(String[] args) {
    SpringApplication.run(Application.class, args);
  }

  @Bean
  public DataSource dataSource() {
    return new DriverManagerDataSource("jdbc:mysql://localhost:3306/test", "root", "password");
  }

  @Bean
  public JdbcTemplate jdbcTemplate(DataSource dataSource) {
    return new JdbcTemplate(dataSource);
  }
}
```

**Ejemplo de CRUD con Spring Data:**

```Java
@Entity
public class User {

  @Id
  @GeneratedValue(strategy = GenerationType.IDENTITY)
  private Long id;

  private String name;

  // ...

}

public interface UserRepository extends JpaRepository<User, Long> {

}
```

```
@Service
public class UserService {

  @Autowired
  private UserRepository userRepository;

  public void saveUser(User user) {
    userRepository.save(user);
  }

  public User getUser(Long id) {
    return userRepository.findById(id).orElse(null);
  }

  public void updateUser(User user) {
    userRepository.save(user);
  }

  public void deleteUser(Long id) {
    userRepository.deleteById(id);
  }

}
```

**En resumen:**

Spring Data es un módulo de Spring Framework que facilita el acceso a datos en diferentes tipos de repositorios de información. Spring Data proporciona una capa de abstracción sobre las API específicas de cada tipo de repositorio, lo que permite a los desarrolladores trabajar con datos de forma uniforme independientemente del tipo de repositorio que se utilice.

**Diferencias entre JpaRepository y CrudRepository**
JPARepository y CrudRepository son interfaces que forman parte de Spring Data JPA.

**CrudRepository:**

Proporciona métodos básicos para operaciones CRUD (Crear, Leer, Actualizar y Eliminar) en entidades.
Es una interfaz más genérica que no depende de JPA.
Se puede usar con cualquier tipo de repositorio que admita operaciones CRUD.

**JpaRepository:**

Extiende CrudRepository y proporciona métodos adicionales específicos de JPA.
<ins>Permite realizar consultas JPQL más complejas.</ins>
Soporta operaciones de borrado en lote.
Ofrece la capacidad de actualizar entidades en cascada.

En resumen:

_CrudRepository: ideal para operaciones CRUD básicas.
JpaRepository: ideal para operaciones CRUD más complejas y que requieren funcionalidades específicas de JPA._

<ins>Tabla comparativa:</ins>

| Característica           | CrudRepository | JpaRepository |
| ------------------------ | -------------- | ------------- |
| Métodos CRUD             | Sí             | Sí            |
| Métodos JPA específicos  | No             | Sí            |
| Consultas JPQL complejas | No             | Sí            |
| Borrado en lote          | No             | Sí            |
| Actualización en cascada | No             | Sí            |

Ejemplo:

```Java
// CrudRepository
public interface UserRepository extends CrudRepository<User, Long> {

}

// JpaRepository
public interface UserRepository extends JpaRepository<User, Long> {

  List<User> findByName(String name);

}
```

En este ejemplo:

La interfaz UserRepository que extiende CrudRepository solo permite operaciones CRUD básicas.
La interfaz UserRepository que extiende JpaRepository permite operaciones CRUD básicas y también permite realizar consultas JPQL como findByName.

¿Cuándo usar cada uno?
Si solo necesitas operaciones CRUD básicas, usa CrudRepository.
Si necesitas realizar operaciones CRUD más complejas o necesitas funcionalidades específicas de JPA, usa JpaRepository.

**Métodos de CrudRepository y JpaRepository**

**CrudRepository:**

- save(): Guarda una entidad en el repositorio.
- get(): Obtiene una entidad del repositorio por su identificador.
- update(): Actualiza una entidad en el repositorio.
- delete(): Elimina una entidad del repositorio.
- findAll(): Obtiene todas las entidades del repositorio.
- existsById(): Comprueba si una entidad con el identificador dado existe en el repositorio.
- count(): Obtiene el número de entidades en el repositorio.

**JpaRepository:**

- findAll(): Obtiene todas las entidades del repositorio ordenadas por el id ascendente.
- findAll(Sort sort): Obtiene todas las entidades del repositorio ordenadas por el campo especificado en el argumento sort.
- findAllById(Iterable<ID> ids): Obtiene todas las entidades del repositorio con los identificadores dados en el argumento ids.
- findById(ID id): Obtiene una entidad del repositorio por su identificador.
- existsById(ID id): Comprueba si una entidad con el identificador dado existe en el repositorio.
- count(): Obtiene el número de entidades en el repositorio.
- delete(T entity): Elimina una entidad del repositorio.
- deleteById(ID id): Elimina una entidad del repositorio por su identificador.
- deleteAll(): Elimina todas las entidades del repositorio.
- flush(): Sincroniza el estado de las entidades en la sesión con la base de datos.
- saveAll(Iterable<T> entities): Guarda todas las entidades del argumento entities en el repositorio.
- saveAndFlush(T entity): Guarda una entidad en el repositorio y sincroniza el estado de la entidad con la base de datos.
- deleteInBatch(Iterable<T> entities): Elimina todas las entidades del argumento entities del repositorio en un solo lote.
- deleteAllInBatch(): Elimina todas las entidades del repositorio en un solo lote.
- findByName(String name): Obtiene todas las entidades del repositorio con el nombre especificado en el argumento name.

**Diferencias entre Spring Data y Spring Data JPA en Spring Boot:**

**Spring Data:**

Es un framework general que proporciona acceso a datos para diferentes tipos de repositorios de datos, como bases de datos relacionales, NoSQL y Hadoop.
No se limita a JPA, también puede trabajar con otras tecnologías de acceso a datos como JDBC, MongoDB, Cassandra, etc.
Ofrece una capa de abstracción sobre las tecnologías de acceso a datos específicas, lo que facilita el desarrollo de aplicaciones que necesitan acceder a diferentes tipos de datos.

**Spring Data JPA:**

Es una implementación específica de Spring Data para JPA.
Se enfoca en el acceso a datos en bases de datos relacionales utilizando JPA.
Proporciona repositorios genéricos para operaciones CRUD y métodos para realizar consultas JPQL.
Facilita el desarrollo de aplicaciones JPA al proporcionar una capa de abstracción sobre la API JPA.

**Conceptos más importantes de Spring Data JPA en Spring Boot:**

1. Entidades:

Clases Java que representan datos en la base de datos.
Se anotan con @Entity.
Deben tener un identificador único.

2. Repositorios:

Interfaces que definen operaciones CRUD (Crear, Leer, Actualizar, Eliminar) sobre entidades.
Se anotan con @Repository.
No es necesario implementarlas, Spring Data JPA crea una implementación por defecto.

3. JPA:

Java Persistence API.
Estándar para el mapeo de objetos a relaciones (ORM) en Java.
Permite trabajar con entidades de forma transparente a la base de datos.

4. Spring Data JPA:

Framework que facilita el uso de JPA en Spring.
Proporciona repositorios genéricos para operaciones CRUD.
Permite realizar consultas JPQL más complejas.

5. Spring Boot:

Framework que facilita el desarrollo de aplicaciones Spring.
Integra Spring Data JPA y lo hace aún más fácil de usar.
Proporciona Starters para la configuración automática de Spring Data JPA.

6. Autoconfiguración:

Característica de Spring Boot que configura automáticamente las beans de Spring en función de las dependencias presentes en el classpath.
Simplifica la configuración de Spring Data JPA en Spring Boot.

7. Anotaciones:

Se utilizan para definir el comportamiento de las entidades y repositorios.
Algunas anotaciones importantes:
@Entity: Indica que una clase es una entidad.
@Repository: Indica que una interfaz es un repositorio.
@Id: Indica el campo que identifica a una entidad.
@GeneratedValue: Indica cómo se genera el valor del identificador de una entidad.

8. Relaciones entre entidades:

Se pueden definir relaciones entre entidades mediante anotaciones.
Algunas relaciones comunes:
Uno a uno (OneToOne)
Uno a muchos (OneToMany)
Muchos a muchos (ManyToMany)

9. Transacciones:

Spring Data JPA gestiona las transacciones automáticamente.
Se pueden definir puntos de control de transacción mediante anotaciones.
@Transactional: Indica que un método debe ejecutarse dentro de una transacción.

10. Consultas JPQL:

Lenguaje de consulta para JPA.
Permite realizar consultas complejas sobre entidades.
Spring Data JPA proporciona métodos para realizar consultas JPQL.

**Métodos de Spring Data JPA**

Spring Data JPA proporciona una amplia gama de métodos para trabajar con entidades y repositorios. A continuación, se presenta una lista de los métodos más importantes:

**Métodos CRUD:**

- save(T entity): Guarda la entidad en la base de datos.
- saveAll(Iterable<T> entities): Guarda todas las entidades en el iterable en la base de datos.
- findById(ID id): Obtiene una entidad por su identificador.
- existsById(ID id): Comprueba si una entidad con el identificador dado existe en la base de datos.
- findAll(): Obtiene todas las entidades de la base de datos.
- findAllById(Iterable<ID> ids): Obtiene todas las entidades con los identificadores dados.
- count(): Obtiene el número de entidades en la base de datos.
- deleteById(ID id): Elimina la entidad con el identificador dado de la base de datos.
- delete(T entity): Elimina la entidad de la base de datos.
- deleteAll(): Elimina todas las entidades de la base de datos.
- deleteAllInBatch(): Elimina todas las entidades del repositorio en un solo lote.
- deleteInBatch(Iterable<T> entities): Elimina todas las entidades del argumento entities en un solo lote.

**Métodos de consulta:**

- findByNombre(String nombre): Busca todas las entidades con el nombre dado.
- findPersonaByEdad(int edad): Busca una persona por su edad.
- findAllByOrderByNombreAsc(): Obtiene todas las entidades ordenadas por nombre ascendente.
- findAllByNombreContaining(String nombre): Busca todas las entidades que contienen el nombre dado.

**Otros métodos:**

- flush(): Sincroniza el estado del repositorio con la base de datos.
- refresh(T entity): Actualiza el estado de la entidad en el repositorio.
- clear(): Elimina todas las entidades del repositorio.
