1. Uno a uno (OneToOne):

Entidad Persona:

```Java
@Entity
public class Persona {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String nombre;

    @OneToOne(mappedBy = "persona")
    private Direccion direccion;

    // Getters and setters
}
```

Entidad Direccion:

```
@Entity
public class Direccion {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String calle;

    private String ciudad;

    @OneToOne
    private Persona persona;

    // Getters and setters
}
```

2. Uno a muchos (OneToMany):

Entidad Persona:

```Java
@Entity
public class Persona {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String nombre;

    @OneToMany(mappedBy = "persona")
    private List<Telefono> telefonos;

    // Getters and setters
}
```

Entidad Telefono:

```Java
@Entity
public class Telefono {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String numero;

    @ManyToOne
    private Persona persona;

    // Getters and setters
}
```

3. Muchos a muchos (ManyToMany):

Entidad Persona:

```Java
@Entity
public class Persona {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String nombre;

    @ManyToMany
    @JoinTable(name = "persona_rol",
        joinColumns = @JoinColumn(name = "persona_id"),
        inverseJoinColumns = @JoinColumn(name = "rol_id"))
    private List<Rol> roles;

    // Getters and setters
}
```

Entidad Rol:

```Java
@Entity
public class Rol {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String nombre;

    @ManyToMany(mappedBy = "roles")
    private List<Persona> personas;

    // Getters and setters
}
```

En estos ejemplos:

Las anotaciones @OneToOne, @OneToMany y @ManyToMany se utilizan para definir las relaciones entre las entidades.
La anotación @JoinColumn se utiliza para especificar la columna de la clave foránea en la tabla secundaria.
La anotación @JoinTable se utiliza para especificar la tabla intermedia en una relación de muchos a muchos.
