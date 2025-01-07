
Geneweaver provides a subset of the data in the GeneWeaver database to make development
against the database easier. The data in the local database is a subset of the data in the
GeneWeaver web application database. 

!!! danger "Out Of Date"
    The database behind the geneweaver web application is updated regularly to stay
    in sync with external data sources. 

    While local database is updated periodically to reflect these changes, it should be
    expected that the local database is **significantly** out of date with respect to 
    the web application database.

    You should also not expect any regularity in the frequency of updates to the local
    database, as is expected with the web application database.

## PostgreSQL RDBMS

The Geneweaver database is designed to be run on the 
[PostgreSQL](https://www.postgresql.org/) RDBMS. You will need to install PostgreSQL
version 11 to run the database. The Geneweaver team is experimenting with higher 
versions of PostgreSQL, but we have not yet verified compatability with versions higher 
than 11.

!!! tip "Postgress.app"
    If you are developing on MacOS, you can use [Postgres.app](https://postgresapp.com/)
    to install PostgreSQL, just make sure to download a version that includes 
    PostgreSQL 11.

### PostgreSQL Setup
You will need to create an empty database for the Geneweaver database. You can do this
using the `createdb` command line tool that comes with PostgreSQL. 

```commandline
createdb geneweaver
```

Optionally, you can also set up users and permissions for the database. For example,
if you want to create a user named `geneweaver` with access to the `geneweaver` 
database, you can do the following:

```commandline
createuser -P geneweaver
createdb -O geneweaver geneweaver
```

## Downloads
The database is available as a schema only, or as both schema and data. Most users will
want to download the schema and data, but if you are only interested in the schema, you
can download that separately.

=== "Schema & Data"
    The schema & data download is available as a single file, `geneweaver.sql`.

    You can either download the file directly from 
    [this link](https://storage.googleapis.com/gwdb-public/geneweaver.sql),
    or you can use the `wget` or `curl` command line tool to download the file.
    === "wget"
        ```commandline
        wget https://storage.googleapis.com/gwdb-public/geneweaver.sql
        ```
    === "curl"
        ```commandline
        curl -O https://storage.googleapis.com/gwdb-public/geneweaver.sql

=== "Schema Only"
    The schema only download is available as a single file, `geneweaver-schema.sql`.

    You can either download the file directly from 
    [this link](https://storage.googleapis.com/gwdb-public/geneweaver-schema.sql),
    or you can use the `wget` or `curl` command line tool to download the file.
    === "wget"
        ```commandline
        wget https://storage.googleapis.com/gwdb-public/geneweaver-schema.sql
        ```
    === "curl"
        ```commandline
        curl -O https://storage.googleapis.com/gwdb-public/geneweaver-schema.sql
        ```

## Installation
Once you have downloaded the database, you can install it using the `psql` command line
tool that comes with PostgreSQL. Make sure that you specify the name of the database
that you created in the steps above.

=== "Schema & Data"
    ```commandline
    psql -d geneweaver -f geneweaver.sql
    ```

=== "Schema Only"
    ```commandline
    psql -d geneweaver -f geneweaver-schema.sql
    ```

## Verification
First, log into the database using the `psql` command line tool. If you set up a specifc
user for the database, you will need to specify the user name and password when logging
in.

```commandline
psql -d geneweaver
```

You can verify that the database was installed correctly by running the following query:

```sql
SELECT COUNT(*) FROM gene;
```
