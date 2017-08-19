1. Each node in the cluster should have access to the database from which the data need to be imported.
2. Make sure mysql client is installed on all the nodes \( datanodes\) in the cluster and have the access to the MySQL server.
3. We need to grant privileges for the IP's of the data nodes at the database end as below:

   GRANTALL PRIVILEGES ON\*.\*TO'user'@'ipadress'



