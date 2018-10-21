# spring4-hibernate5-no-xml-integration

This project represents a great example for Hibernate 5 integration with Spring 4. It's awesome, because it uses the @Autowired and other nice annotations, which at the end make the use of .xml configurations not necessary.
The DB connectivity details are in the db.properties file.

If following the 1) reference, then besides it's setup, you need to provide:
“db.properties:
// MySQL properties
db.url=jdbc:mysql://localhost:3306/BORAJI?useTimezone=true&serverTimezone=UTC
// Hibernate properties
hibernate.dialect=org.hibernate.dialect.MySQLDialect
AppConfig:
getSessionFactory() method:
props.put("hibernate.dialect", env.getProperty("hibernate.dialect"));”

The secret of the above project configuration lays in the local “AppConfig” class, at the “LocalSessionFactoryBean” class:
“FactoryBean that creates a Hibernate SessionFactory. This is the usual way to set up a shared Hibernate SessionFactory in a Spring application context; the SessionFactory can then be passed to Hibernate-based data access objects via dependency injection.” - because the “UserDaoImp” class has:

“   @Autowired
   private SessionFactory sessionFactory;
“
which the docs exactly relate to when they say “SessionFactory can then be passed to Hibernate-based data access objects via dependency injection”.

References:
1) https://www.boraji.com/spring-4-hibernate-5-integration-example-with-zero-xml
