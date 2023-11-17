## ldentifier Generator

All the generator classes implement the org.hibernate.id.ldentifierGenerator interface. 

The application programmer may create one's own generator classes by implementing the IdentifierGenerator interface. 



Hibernate framework provides many built-in generator classes :

1. **assigned**: Default, value has to be explicitly assigned to persistent object before persisting it. generator class = assigned

<br>

2. **increment**: It increments value by 1. It generates short, int, or long type identifier. 

<br>

3. **native**: It uses identity, sequence, or hilo, depending on the database vendor. 

<br>

4. **sequence**: It uses the sequence of the database. If there is no sequence defined, it creates a sequence automatically. For example, in case of Oracle database, it creates a sequence named HIBERNATE_ SEQUENCE. 

<br>

5. **hilo**: It uses high and low algorithm to generate the id of type short, int, and long. 

<br>

6. **identify**: It is used in Sybase, My SQL, MS SQL Server, DB2, and SQL to support the id column. The returned id is of type short, int, or long. 
