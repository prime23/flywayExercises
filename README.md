#Simple Flyway Exercise

The point of this project is to try out [Flyway](https://flywaydb.org/) database migrations, some of the exercise I will be creating will try edge cases/ cause errors.

To change which set of migrations run go into application.properties and change the flyway.locations to db/migration{d} where d is the migration number or left off completely for the very basic migration example

####Example 1
db/migration - most basic example, only migration is run

####Example 2
db/migration2 - a very basic example with two migrations

####Example 3
db/migration3 - slightly malformed example migration skips V2__{descriptions}.sql, still works. It worth running
```SQL
SELECT * FROM "schema_version"
```

in the h2 web console and look at the resulting table.

####Example 4
Simple example with a subversion migration.

####Example 5
Two migrations evaluate to version 2. An error occurred as should be expected. Fairly good error message also
```
Caused by: org.flywaydb.core.api.FlywayException: Found more than one migration with version 2
Offenders:
-> {locationOfProject}/flyway/target/classes/db/migration5/V2__roles.sql (SQL)
-> {locationOfProject}/flyway/target/classes/db/migration5/V2_0__alter_roles.sql (SQL)
```

####Example 6
For fun tried to do a version with letters, did not expect it to work and it did not, still a good error message was produced
```
Caused by: org.flywaydb.core.api.FlywayException: Invalid version containing non-numeric characters. Only 0..9 and . are allowed. Invalid version: a
```