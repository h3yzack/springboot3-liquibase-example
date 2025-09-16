# Spring Boot 3 Liquibase Example

This project demonstrates how to use Liquibase with Spring Boot 3 to manage database schema changes and generate SQL diff scripts from JPA entities. Both Gradle and Maven build settings are included, so either tool can be used to generate changelogs and apply updates to the database.

## Requirements

- Java 21
- PostgreSQL Database
- Gradle 8.5+ or Maven 3+

## Dependencies

- Spring Boot 3.5.5
- Liquibase Core 4.31.1
- Liquibase Hibernate 4.31.1
- PostgreSQL JDBC Driver 42.7.7
- Lombok (optional, for code generation)

## Usage

### Start the Service

```sh
./mvnw spring-boot:run
# or
./gradlew bootRun
```

### Generate Database Changelog and SQL Diff

#### With Gradle

- Generate a diff changelog SQL file (from current DB and entities):

  ```sh
  ./gradlew diffChangeLog -Pdiff.version=1.0.0 -Pauthor=example
  ```
  This will create a file like `src/main/resources/db/changelog/migration/_1.0.0_migrate.sql`.

- Apply the changelog to the database:

  ```sh
  ./gradlew update
  ```

#### With Maven

- Generate a diff changelog SQL file:

  ```sh
  ./mvnw liquibase:diff -Ddiff.version=1.0.0
  ```
  The generated file will be in `src/main/resources/db/changelog/migration/_1.0.0_migrate.sql`.

- Apply the changelog to the database:

  ```sh
  ./mvnw liquibase:update
  ```

## Notes

- Database connection and Hibernate settings are configured in `src/main/resources/liquibase.properties`.
- The changelog master file is at `src/main/resources/db/changelog/db.changelog-master.yaml` and includes all migration scripts in the `migration` folder`.