https://community.hortonworks.com/questions/66961/how-sqoop-internally-works.html

 Sqoop is building a SQL query \(actually one for each mapper\) to the source table it is ingesting into HDFS from. The number of mappers \(default is four, but you can override\) leverage the split-by column and basically Sqoop tries to build an intelligent set of WHERE clauses so that each of the mappers have a logical "slice" of the target table. As and example, if we used three mappers and a split-by column that is an integer with ranges from 0 to 1,000,000 for the actual data \(i.e. sqoop can do a pretty easy min and max call to the DB on the split-by column\), then Sqoop first mapper would try to get values 0-333333, the second mapper would pull 333334-666666, and the last would grab 666667-1000000.

