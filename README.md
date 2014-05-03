# Cassandra JMeter Plugin for Cassandra

---
A CQL3 native plugin for Cassandra 2.0 using the DataStax Java Driver for Apache Cassandra. The plugin is loosely based on the JDBC Plugin included with JMeter originally written by Ruben Laguna. It includes 4 components:

- Cassandra Configuration
- Cassandra Sampler
- Cassandra PreProcessor
- Cassandra PostProcessor


## Installation

Simply drop the JMeterCassandra.jar into the JMeter's lib dirctory, and its dependent libraries in the the lib/ext directory.

## Configuration

Because it is based on the Java Driver, the plugin automatically connects to a given contact point and will discover the rest of the nodes in the cluster.  To function correclty, it is necessary that JMeter be able to directly access all of the nodes in your cluster

Fields:
- Variable Name (Required): Similar to JDBC.  A name by which the Samplers/Processors will refer to this connection
- Contact Points (Required):  A comma-separated list of contact points in your cluster
- Default Keyspace (Optional):  The default keyspace used by CQL
- Username (Future):
- Password (Future):


![alt text](https://raw.githubusercontent.com/slowenthal/jmeter-cassandra/master/wiki/images/configScreenShot.png)

# Sampling

Simple add a Cassandra Sampler to your test plan.  The sampler runs in 3 modes, Simple Statement, Prepared Statement, Batch Statement.

Set up the following fields:

- Session Variable - the variable name created in the Cassandra Connection
- Query Type - Simple Statement, Prepared Statement, Batch Statement.  The Batch Statement is a dynamic batch, and is not related to the BEGIN BATCH statment.
- CQL Query - A single CQL query.  You may use DML, DDL, BEGIN BATCH, SELECT, etc.  If the query types is Prepared or Batch, you may use parameter markers in the query.
- Parameter Values (Optional):  The parameter values used in Prepared and Batch statements. See the JDBC Sampler for more information.
- Variable Names (Optional):  Variables created for output values.  The names specified are postpended with the row number.  For example, if you have a variable call LAST_NAME, and the result set outputs 3 rows, the sampler outputs 3 variables - LASTNAME_1, LASTNAME_2, LASTNAME_3.










