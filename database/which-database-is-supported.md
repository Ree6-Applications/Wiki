# Which Database is supported?

## Note

We use Flyway to migrate Database schemas to a newer version, this allows us to update the Database without forcing completely breaking changes. For Database Version that are being supported by Flyway check out this [page](https://documentation.red-gate.com/flyway/flyway-cli-and-api/supported-databases).

### MariaDB

The official Ree6 bot is using MariaDB and it is our main testing suit, so we recommend using MariaDB.

### SQLite

SQLite allows you to have a single file as your Database, we sadly currently do not recommend using it because of some Issues related to Flyway.

### H2

H2 is similar to SQLite but allows the creating of an embedded Server to allow multiple Applications to access the same Database.

### PostgreSQL

Postgre is a simple and efficient Database solution it's not like H2 or SQLite but rather like MariaDB. If using MariaDB is not an option for you, PostgreSQL is the way to go.
