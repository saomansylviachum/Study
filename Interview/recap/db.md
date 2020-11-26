# Questions
1. What do you know about JDBC?
    
    - JDBC refers to "Java DataBase Conectivity". It's an API that enables Java applications to interact with database.
    - There are 4 key components in JDBC: DriverManager, Connection, Statement, Resultset, DatabaseMetaData
    - There are also different driver in JDBC:
        - JDBC-ODBC Bridge
        - Native API driver
        - Network Protocol Driver
        - Database Protocol Driver(Connects directly to database without any native code or middle tier)

2. What about the different between JDBC statement?
		There are different statement in JDBC: 
		preparedStatement that we don't directly put the plain text parameter in the query, instead we insert the parameter later in the procedure.
		callableStatement: we calls some pre-stored procedure in the database
		
3. 

