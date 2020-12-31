[Using Flashback Database and Restore Points](https://docs.oracle.com/cd/E11882_01/backup.112/e10642/flashdb.htm#BRADV71000)
FLASHBACK DATABASE TO RESTORE POINT 'before_upgrade';
FLASHBACK DATABASE TO SCN 202381;
CREATE RESTORE POINT before_upgrade;
CREATE RESTORE POINT before_upgrade GUARANTEE FLASHBACK DATABASE;
RMAN> LIST RESTORE POINT ALL;
SQL> DROP RESTORE POINT before_app_upgrade;
ALTER SYSTEM SET DB_FLASHBACK_RETENTION_TARGET=4320; # 3 days
By default DB_FLASHBACK_RETENTION_TARGET is set to 1 day (1440 minutes).
ALTER DATABASE FLASHBACK ON;
Optionally, disable flashback logging for specific tablespaces:
ALTER TABLESPACE tbs_3 FLASHBACK OFF;

[Managing Archived Redo Logs](https://docs.oracle.com/cd/B19306_01/server.102/b14231/archredo.htm)
SHUTDOWN
Back up the database.
STARTUP MOUNT
ALTER DATABASE ARCHIVELOG;
ALTER DATABASE OPEN;
SHUTDOWN IMMEDIATE
Back up the database.

[RMAN Incremental Backups](https://docs.oracle.com/cd/B19306_01/backup.102/b14192/bkup004.htm)

[How to Restore Oracle Database using RMAN (with Examples)](https://www.thegeekstuff.com/2014/11/oracle-rman-restore/)