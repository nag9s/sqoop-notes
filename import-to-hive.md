1. SQOOP can automatically populate the metadata for you in hive. If the table in Hive does not exist yet, Sqoop will simply create it based on the metadata fetched for your table or query. If the table already exists, Sqoop will import data into the existing table.
2. Sometimes the default mapping doesn’t work correctly for your needs; in those cases,
   you can use the parameter --map-column-hive to override it. 



