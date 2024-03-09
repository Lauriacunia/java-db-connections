**JDBC (Java Database Connectivity)** es la API estándar de Java para acceder a bases de datos relacionales. Permite realizar operaciones como:

**Conexión a la base de datos:**

```java
Connection connection = DriverManager.getConnection("jdbc:mysql://localhost:3306/mydb", "root", "password");
```

**Ejecución de consultas SQL:**

```Java
Statement statement = connection.createStatement();
ResultSet resultSet = statement.executeQuery("SELECT * FROM users");

while (resultSet.next()) {
  System.out.println(resultSet.getString("name"));
}
```

**Actualización de datos:**

```
PreparedStatement preparedStatement = connection.prepareStatement("UPDATE users SET name = ? WHERE id = ?");
preparedStatement.setString(1, "John Doe");
preparedStatement.setInt(2, 1);
preparedStatement.executeUpdate();
```

**Inserción de datos:**

```
PreparedStatement preparedStatement = connection.prepareStatement("INSERT INTO users (name, email) VALUES (?, ?)");
preparedStatement.setString(1, "Jane Doe");
preparedStatement.setString(2, "jane.doe@example.com");
preparedStatement.executeUpdate();
```

**Eliminación de datos:**

```Java
PreparedStatement preparedStatement = connection.prepareStatement("DELETE FROM users WHERE id = ?");
preparedStatement.setInt(1, 1);
preparedStatement.executeUpdate();
```

**Conceptos clave de JDBC:**

- _DriverManager_: Se encarga de gestionar las conexiones a las bases de datos.
- _Connection_: Representa una conexión a una base de datos.
- _Statement_: Se utiliza para ejecutar consultas SQL.
- _ResultSet_: Contiene los resultados de una consulta SQL.
- _PreparedStatement_: Se utiliza para ejecutar consultas SQL con parámetros.
