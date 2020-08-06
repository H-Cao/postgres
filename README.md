# Extended PostgreSQL embedded Python API

## Description
This branch in based on  [postgres:REL_12_STABLE](https://github.com/postgres/postgres/tree/REL_12_STABLE). To optimize the conversion operation of [AIDA DB Adapter for PostgreSQL](https://github.com/joedsilva/AIDA/tree/postgresqlAdapter),  a function called **execute_and_convert_to_columns** was added to the plpy module. This function will produce a column-based resultset instead of row-based ones. 
 
 ## Usage
 ```python
 CREATE FUNCTION demo()
 RETURNS void AS $$
     ...
     result = plpy.execute_and_convert_to_columns( query [, max-rows] )
     ...
$$ LANGUAGE plpython3u;
 ``` 

## Build
```
./configure --prefix=PREFIX --exec-prefix=EXEC-PREFIX --with-includes=< where NumPy is installed >/numpy/core/include  --with-python PYTHON=< location of python3 >
make && make install
```
After start the Postgres server.
```
psql -d template1 -c  "CREATE LANGUAGE plpython3uC;"
psql -d template1 -c "UPDATE pg_language SET lanpltrusted = true  WHERE lanname LIKE 'plpython3u';"
```



## Original README File

<br>

PostgreSQL Database Management System

<br>

This directory contains the source code distribution of the PostgreSQL
database management system.

<br>

PostgreSQL is an advanced object-relational database management system
that supports an extended subset of the SQL standard, including
transactions, foreign keys, subqueries, triggers, user-defined types
and functions.  This distribution also contains C language bindings.

<br>

PostgreSQL has many language interfaces, many of which are listed here:

	[https://www.postgresql.org/download](https://www.postgresql.org/download)

See the file INSTALL for instructions on how to build and install
PostgreSQL.  That file also lists supported operating systems and
hardware platforms and contains information regarding any other
software packages that are required to build or run the PostgreSQL
system.  Copyright and license information can be found in the
file COPYRIGHT.  A comprehensive documentation set is included in this
distribution; it can be read as described in the installation
instructions.

<br>

The latest version of this software may be obtained at
[https://www.postgresql.org/download/](https://www.postgresql.org/download/).  For more information look at our
web site located at [https://www.postgresql.org/](https://www.postgresql.org/).
