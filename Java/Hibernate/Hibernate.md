### steps to use Hibernate :
1. create **org.hibernate.cfg.configuration** object
2. load the Meta information
3. create **org.hibernate.SessionFactory** object
4. make hibernate API call on session object
5. close the session
6. close the sessionFactory object

### Hibernate Architecture :
<br>

![Hibernate Architecture](./assets/01%20-%20Hibernate%20Architecture.png)
<br>

each session Object has three lifecycle.
[Here read more.](./chapters/Hibernate%20Lifecycle.md)


### Hibernate cores :
1. Configuration (org.configuration.cfg) : it gives two services in hibernate 
    + Loads mapping file and configuration file into memory and makes them available to hibernate engine 
    + Acts as factory to create the SessionFactory 

<br>

2. SessionFactory (org.hibrnate.SessionFactory) 
    - Hibernate (engine) implements SessionFactory interface 
    + SessionFactory is one per DBMS (mostly one per application)
    + SessionFactory is Thread safe 
    + SessionFactory is not a Singleton 
    + It creates Session object, SessionFactory encapsulates, second level cache, connection pool, meta information cache, and pool of session 

<br>

3. Session (org.hibernate.Session) 
    + Hibernate engine implements Session interface 
    + Session object acts as persistent manager 
    + Session object is a light weight object 
    + It encapsulates connection and first-level cache  
    + Session object is not thread-safe 
    + In every DAO method, Session object is created 
    + It is used for CRDD operation 

<br>

4. Transaction (org.hibernate.Transaction) 
    + Hibernate engine implements this interface 
    + When database connection is created by hibernate, connection associated with session is in autocommit disable mode. 
    + Whenever any CRUD operation is performed, the changes will not be reflected in the database unless connection is maintained in auto-commit enabled mode. 

<br>

5. ldentifier Generator
    + [read more here](chapters/ldentifierGenerator.md)