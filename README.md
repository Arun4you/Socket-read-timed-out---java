# Socket-read-timed-out---java

This feature is specific to the Oracle JDBC driver. 
It sets a timeout on the Socket level for the JDBC thin driver. 
By setting up the socket timeout, you can prevent the infinite waiting situation when there is a network error and shorten the failure time.
Once the socket read timeout occurs, the JDBC driver throws a java.sql.SQLRecoverableException: IO Exception: Socket read timed out.
oracle.jdbc.ReadTimeout=50000ms (It works for Oracle JDBC driver version 11g and later)
The socket timeout value must be higher than the statement timeout value. If the socket timeout value is smaller than the statement timeout value, as the socket timeout will be executed first, and the statement timeout value becomes meaningless and will not be executed.

