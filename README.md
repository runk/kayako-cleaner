kayako-cleaner
==============

Script allows you to purge old data from kayako database (Kayako helpdesk solution, http://kayako.com/).

### Usage
Usage is pretty easy, you have to run something like this:
```shell
    $ mysql -D kayakodb -u dbuser -p < cleaner.sql
```

### Configuration 

By default this script removes all tickets **older than 90 days**. The point is in editing the query that collects ticket 
ids, so if you want any complex criteria - write it here: 

```sql
    INSERT INTO ticketids(ticketid) 
    SELECT ticketid FROM swtickets WHERE (dateline + (86400 * 90) < UNIX_TIMESTAMP(NOW()));
```  

  
