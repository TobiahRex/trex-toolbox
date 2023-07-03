# [Home](../README.md) > Postgress & SQL

1. Open the Server Dashboard
    ```bash
    /Applications/Postgres.app/Contents/Versions/12/bin/psql -p5434 "trex"
    ```
    Here is the converted list with numerical list formatting and code snippets in ```bash syntax:

2. Describe users
   ```bash
   \du+
   ```

2. List databases
   ```bash
   \l+
   ```

3. Drop a database
   ```bash
   DROP DATABASE database_name;
   ```

4. Drop a user
   ```bash
   DROP USER name;
   ```

5. Create a user
   ```bash
   CREATE USER toby WITH PASSWORD 'Password';
   ```

6. Create a database
   ```bash
   CREATE DATABASE database_name;
   ```

7. Grant access to database for a user
   ```bash
   GRANT ALL PRIVILEGES ON DATABASE database_name to toby;
   ```

8. Login as user toby
   ```bash
   psql -U toby
   ```

9. Login to the "trex" server
   ```bash
   psql -p5434 'trex'
   # NOTE: You need this syntax even for local database access.
   ```

10. Change password of user
    ```bash
    ALTER USER user_name WITH PASSWORD 'New Password';
    ```

11. Restore database from backup
    ```bash
    pg_restore -p5434 -S trex -d fun ~/Downloads/example.dump
    # -p5434 is the active Postgres server port
    # -S is the Super User flag
    # -d is the database name to dump to (should already exist)
    # file is the dump file content
    ```

12. Show tables & size of table
    ```bash
    \d+
    ```

13. Show queryable data
    ```bash
    \d+ table_name
    # Fields in column can be queried
    ```

14. Select data
    ```bash
    SELECT column_1, column_2
    FROM database_name
    WHERE column_1 < some_value;
    ```

15. Intersecting data from 2 tables
    ```bash
    SELECT table_1.column_1, table_2.column_2
    FROM table_1, table_2
    WHERE table_1.some_id = table_2.some_id
    # The value in WHERE doesn't matter the order, it's simply a "connection" between the two tables
    ```

16. Connect to a remote server
    ```bash
    psql -h <host> -p <port> -U <user_name> -d <database_name>
    Password for user <user_name>: <Password>
    # Default port = 5432
    ```

17. Modify data in a table cell
    ```bash
    UPDATE table_name
    SET column1 = value1, column2 = value2
    WHERE condition;
    ```

18. Dump Table to File
    ```bash
    pg_dump -h <host> -U <username> -p <Port> -F <format> -f <output file name> -d <db name> -t public.<tablename>
    # Format (-F) can either be "d" or "p". "d" is for "directory" and seems to work for restoration of tables, whereas "p" is better for archival backup without restoration requirements.
    ```

19. Load Table from File
    ```bash
    pg_restore -h <host> -U <username> -p <Port> -d <db name> -t <table name> -v <file containing dump>
    ```

20. JOIN between 2 tables
    ```bash
    SELECT t.*
    FROM fds.sym_v1_sym_sec_entity_hist t1
    LEFT JOIN fds.sym_v1_sym_sec_entity t2 on t2.factset_entity_id = t1.factset_entity_id
    WHERE t2.factset_entity_id IS NULL
    ```