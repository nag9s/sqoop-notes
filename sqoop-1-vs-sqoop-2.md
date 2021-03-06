Sqoop 2 is being deprecated. Customers are advised to use Sqoop 1 instead. - From Cloudera blog \([https://www.cloudera.com/documentation/enterprise/5-4-x/topics/cdh\_ig\_sqoop\_vs\_sqoop2.html\](https://www.cloudera.com/documentation/enterprise/5-4-x/topics/cdh_ig_sqoop_vs_sqoop2.html%29\)

```
      As of Dec'16 there is no stable release of SQOOP2 
```

[Apache Sqoop](http://sqoop.apache.org/) \(Sqoop 1x\)  uses a client model where the user needs to the install Sqoop along with connectors/drivers on the client. Sqoop2 \(the next version of Sqoop\) uses a service based model, where the connectors/drivers are installed on the Sqoop2 server. Also, all the configurations needs to be done on the Sqoop2 server. Note that this blog entry refers to **Sqoop 1x \(client based model\) as Sqoop and Sqoop 2x \(service based model\) as Sqoop2.**

From an MR perspective another difference is that Sqoop submits a Map only job, while Sqoop2 submits a MapReduce job where the Mappers would be transporting the data from the source, while the Reducers would be transforming the data according to the source specified. This provides a clean abstraction. In Sqoop, both the transportation and the transformations were provided by Mappers only.

Another major difference in Sqoop2 is from a security perspective. The administrator would be setting up the connections to the source and the targets, while the operator user uses the already established connections, so the operator user need not know the details about the connections. And operators will be given access to only some of the connectors as required.

Sqoop2 is still **half cooked **and a lot more to be improved/developed from a usability/documentation perspective. Although the features of Sqoop2 are interesting, until Sqoop2 becomes more usable/stable we are left with Sqoop to get the data from RDBMs to Hadoop.

In Sqoop, who have access to the hadoop cluster will know the database credentials as it has to be hard coded

* In Sqoop2, database credentials will be known to only the admins who manage the cluster. Developers need not know the password.
* In Sqoop client can submit jobs directly on the cluster, there is no server concept. It means that you need to have JDBC jar files on the Sqoop client. Once you have database credentials and the jar files with in the same firewall, security can be easily breached outside Sqoop.
* In Sqoop2 client will not submit jobs directly, it will point to the server and server will submit the jobs. So Sqoop server, database and hadoop cluster can be behind the firewall and only Sqoop server ports shall be opened to only Sqoop2 client. Hence users cannot breach security by logging into database outside the Sqoop \(even if they know database credentials and have jdbc jars\).

On top of additional security, it also have this major difference:

* Sqoop cannot be integrated with web interfaces such as hue as it follows client only architecture
* Sqoop2 runs on client server architecture. Server runs as web applications and hence tools like Hue can actually used to develop sqoop based scripts



