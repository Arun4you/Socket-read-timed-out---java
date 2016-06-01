# Socket-read-timed-out---java

This feature is specific to the Oracle JDBC driver. 

It sets a timeout on the Socket level for the JDBC thin driver. 

By setting up the socket timeout, you can prevent the infinite waiting situation when there is a network error and shorten the failure time.

Once the socket read timeout occurs, the JDBC driver throws a java.sql.SQLRecoverableException: IO Exception: Socket read timed out.

oracle.jdbc.ReadTimeout=50000ms (It works for Oracle JDBC driver version 11g and later)

The socket timeout value must be higher than the statement timeout value. 

If the socket timeout value is smaller than the statement timeout value, as the socket timeout will be executed first, and the statement timeout value becomes meaningless and will not be executed.

What is socket timeout:

Java networking is, by default, a form of blocking I/O. Thus, when a Java networking application reads from a socket connection, it will generally wait indefinitely if there is no immediate response. If no data is available, the program will keep waiting, and no further work can be done. One solution, which solves the problem but introduces a little extra complexity, is to have a second thread perform the operation; this way, if the second thread becomes blocked the application can still respond to user commands, or even terminate the stalled thread if necessary.

