# Resolving MySQL Error: `ERROR 1290 (HY000)` When Using `INTO OUTFILE`

Export tables from the database using the following SQL statement
```
SELECT * FROM raw_events INTO OUTFILE ‘$absolute_path/runoob.txt’;
```
If you encounter the following error

```
ERROR 1290 (HY000): The MySQL server is running with the --secure-file-priv option so it cannot execute this statement
```

Follow these steps to resolve it:

1. Edit the MySQL configuration file:

```bash
vi /usr/local/etc/my.cnf
```

2. Under the `[mysqld]` section, add the following line:

```ini
secure_file_priv=''
```

3. Restart the MySQL server:

```bash
mysql.server restart
```

This will allow the `INTO OUTFILE` statement to execute without restriction.
