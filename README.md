# Spring Boot 3 with Liquibase
Spring Boot 3 with Liquibase example project - to generate database changelog and generate sql script from entity

### Requirements
- Maven 3+
- Java 19
- Postgresql Database

### Dependency
- Spring Boot 3.0.3
- Liquibase Maven Plugin 4.19.0

### Use cases
#### Start the service
```
mvn spring-boot:run
```
#### Generate diff changelog 
```
mvn liquibase:diff -Ddiff.version=1.0