1. SQOOP can automatically populate the metadata for you in hive. If the table in Hive does not exist yet, Sqoop will simply create it based on the metadata fetched for your table or query. If the table already exists, Sqoop will import data into the existing table.

                 `  sqoop import \

   \`                                     `--connect jdbc:mysql://mysql.example.com/sqoop \`

                                            `--username sqoop \`

                                              `--password sqoop \`

                                               `--table cities \`

                                                `--hive-import`

1. Sometimes the default mapping doesn’t work correctly for your needs; in those cases, you can use the parameter --map-column-hive to override it. 
2. This parameter expects  a comma-separated list of key-value pairs separated by the equal sign \(=\) in order to  specify which column should be matched to which type in Hive. For example, if you  want to change the Hive type of column id to STRING and column price to DECIMAL, you can specify the following Sqoop parameters:



