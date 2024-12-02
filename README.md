# Big-data-project
teammate: ChengRan Sun, Hao Lan, Zhou Ye

# 1. Software Requirement

- windows:

  | software | version   |
  | -------- | --------- |
  | hadoop   | 3.3.6     |
  | java     | 8         |
  | hive     | 3.1.3     |
  | derby    | 10.14.2.0 |

- Mac
  | software | version   |
  |----------|-----------|
  | hadoop   | 

# 2. Installing spark

- spark-class org.apache.spark.deploy.master.Master
- spark-class2.cmd org.apache.spark.deploy.worker.Worker spark://IP:PORT



# 3. Installing hive

(https://medium.com/republic-of-coders-india/guide-to-install-and-run-hive-3-1-2-on-windows-10-f7d778157904)

1. extract derby using 7-zip

2. extract hive

3. copy all jar files under `\derby\lib` to `hive\lib`

4. create `hive-site.xml` under `hive\conf` and edit the content(create hive\tmp folder for one of the configuration):

   ```xml
   <?xml version="1.0"?>
   <?xml-stylesheet type="text/xsl" href="configuration.xsl"?>
   <configuration>
           <property>
               <name>javax.jdo.option.ConnectionURL</name>
               <value>jdbc:derby://localhost:1527/metastore_db;create=true</value>
               <description>JDBC connect string for a JDBC metastore</description>
           </property>
   
           <!-- <property>
               <name>system:java.io.tmpdir</name>
               <value>%HIVE_HOME%/tmp</value>
           </property> -->
   
           <!-- <property>
               <name>system:user.name</name>
               <value>${user.name}</value>
           </property> -->
   
           <property>
               <name>javax.jdo.option.ConnectionDriverName</name>
               <value>org.apache.derby.jdbc.ClientDriver</value>
               <description>Driver class name for a JDBC metastore</description>
           </property>
   
           <property>
               <name>hive.metastore.warehouse.dir</name>
               <value>/user/hive/warehouse</value>
               <description>Location of default database for the warehouse</description>
           </property>
   
           <property>
               <name>hive.server2.enable.doAS</name>
               <value>true</value>
               <description>Enable user impersonation for HiveServer2</description>
           </property>
   
           <property>
               <name>hive.server2.authentication</name>
               <value>NONE</value>
               <description>Client authentication types. NONE: no authentication check LDAP: LDAP/AD based authentication KERBEROS: Kerberos/GSSAPI authentication CUSTOM: Custom authentication provider (Use with property hive.server2.custom.authentication.class)</description>
           </property>
   
           <property>
               <name>datanucleus.autoCreateTables</name>
               <value>true</value>
               <description>Auto-create tables in the metastore</description>
           </property>
   
   </configuration>
   ```

   

5. add env variable:

   - HIVE_HOME
   - DERBY_HOME
   - HIVE_LIB
   - HIVE_BIN
   - HADOOP_USER_CLASSPATH_FIRST: true

6. (optional:) copy `hadoop\share\hadoop\common\lib\guava-27.0-jre.jar` into `hive\lib\guava-27.0-jre.jar`

7. replace hive\bin folder with "https://svn.apache.org/repos/asf/hive/trunk/bin/"(https://stackoverflow.com/questions/42958213/install-hive-on-windows-hive-is-not-recognized-as-an-internal-or-external-com)( PS: there is also schemaTool.cmd)

8. 

9. Run `hive --service  schematool -dbType derby -initSchema`





# *. Useful commands

- windows:

  - find the PID of process occupying a port: netstat -ano | findstr :<port_number> 
  - taskkill /PID $PID /F

  
