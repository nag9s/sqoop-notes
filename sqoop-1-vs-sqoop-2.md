Sqoop 2 is being deprecated. Customers are advised to use Sqoop 1 instead. - From Cloudera blog \([https://www.cloudera.com/documentation/enterprise/5-4-x/topics/cdh\_ig\_sqoop\_vs\_sqoop2.html\](https://www.cloudera.com/documentation/enterprise/5-4-x/topics/cdh_ig_sqoop_vs_sqoop2.html%29\)

[Apache Sqoop](http://sqoop.apache.org/) \(Sqoop 1x\)  uses a client model where the user needs to the install Sqoop along with connectors/drivers on the client. Sqoop2 \(the next version of Sqoop\) uses a service based model, where the connectors/drivers are installed on the Sqoop2 server. Also, all the configurations needs to be done on the Sqoop2 server. Note that this blog entry refers to **Sqoop 1x \(client based model\) as Sqoop and Sqoop 2x \(service based model\) as Sqoop2.**

From an MR perspective another difference is that Sqoop submits a Map only job, while Sqoop2 submits a MapReduce job where the Mappers would be transporting the data from the source, while the Reducers would be transforming the data according to the source specified. This provides a clean abstraction. In Sqoop, both the transportation and the transformations were provided by Mappers only.

Another major difference in Sqoop2 is from a security perspective. The administrator would be setting up the connections to the source and the targets, while the operator user uses the already established connections, so the operator user need not know the details about the connections. And operators will be given access to only some of the connectors as required.

Sqoop2 is still **half cooked **and a lot more to be improved/developed from a usability/documentation perspective. Although the features of Sqoop2 are interesting, until Sqoop2 becomes more usable/stable we are left with Sqoop to get the data from RDBMs to Hadoop. 

