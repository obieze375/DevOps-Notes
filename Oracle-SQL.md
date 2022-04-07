

# Create table 

~~~

The syntax to create a table is:
CREATE TABLE [table name]
      ( [column name] [datatype], ... );

 CREATE TABLE employee
       (id int, name varchar(20));
~~~
# Drop table  

~~~  

drop tablename;


~~~ 

# Describe Table  

~~~  
SQL> desc dba_tables;
 Name                                      Null?    Type
 ----------------------------------------- -------- ----------------------------
 OWNER                                     NOT NULL VARCHAR2(30)
 TABLE_NAME                                NOT NULL VARCHAR2(30)
 TABLESPACE_NAME                                    VARCHAR2(30) 


SQL> desc request; 
REQUEST_NUMBER                        DESCRIPTION              REQUEST_NAME 
______________________________________________________ 

 
~~~

# Select from table  

~~~  

select * from <table_name>; 



~~~

# Commit changes 

~~~ 

commit; 

~~~

# Check DB name 

~~~  

SQL> select name from v$database;

~~~ 

# Check name of instance 

~~~  

SQL>Select name from v$instance; 

~~~ 

# Check owner of table 


~~~ 
select OWNER from dba_tables where TABLE_NAME='REQUEST'; 
~~~ 

# Check Remote listener 

~~~ 
2021-02-08 16:09:52 - SQL> show parameter remote_listener;
~~~ 

# Create Tablespace 

~~~ 
create tablespace <tsname> datafile '+<diskgroup>' size 1m
autoextend on next 50m maxsize unlimited
extent management local autoallocate
segment space management auto;
~~~ 

# Drop Tablespace 

~~~ 

drop tablespace;  

~~~ 

