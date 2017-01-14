# Overview
If you want to connect your external database query or visualization tool to Hive you have to copy jars from the Hadoop cluster to your PC where it can be read by a tool. Within this maven project you can easily pull the required jars that depend on you cloudera cluster version. Provided project can be use with non-secure and secure (kerberos) cloudera cluster.
If you need more information about Hiver Server please check:
[Hiveserver2 Client Documentation](https://cwiki.apache.org/confluence/display/Hive/HiveServer2+Clients#HiveServer2Clients-JDBC).


To run maven you need java. I was using JDK-8u60. Be sure that "JAVA_HOME" environment varialbe is set up coretly and points to your JDK installation. 


To use this project you have to install [Apache Maven]{https://kainossoftwareltd-my.sharepoint.com/personal/andrzejj_kainos_com/_layouts/15/guestaccess.aspx?docid=08fc5916c169d4d75bbb0d6cefb8d6fbe&authkey=AebWILMYi-f8BGdIKsJHYBQ&expiration=2017-01-27T23:23:18.000Z}. I used version 3.3.9 during testing. For windows after maven installation you have to add two evironment variables:
```
M2_HOME=C:\PathToMavenDir
MAVEN_HOME=C:\PathToMavenDir
```
where "C:\PathToMavenDir" is maven directory that contain bin directory. Also, you have to add to windows system PATH:
```
;%M2_HOME%\bin
```
TO verify maven installation just run in command line:
```
mvn -version
```

## IntelliJ Data Grip (2016.3.1 version)
Below is an example configuration using IntelliJ [Data Grip](https://www.jetbrains.com/datagrip/):

1. Under "File" > "Data Sources...", first create a new Driver called Hive. 
Default url template is as follows: "jdbc:hive2://{host}:{port}/{database}[;<;,{:identifier}={:param}>]" 

![](https://github.com/andrzej-jedrzejewski/hive-jdbc-cloudera-jar/blob/master/images/driver_conf_masked.png)

2. Then create a new Project Data Source using the new Driver.

![](https://github.com/andrzej-jedrzejewski/hive-jdbc-cloudera-jar/blob/master/images/data_source_conf_1_masked.png)

3. Then change jvm advanced option ("-Dsun.security.krb5.debug=true -Djavax.security.auth.useSubjectCredsOnly=false") for new Data Source.
![](https://github.com/andrzej-jedrzejewski/hive-jdbc-cloudera-jar/blob/master/images/data_source_conf_2_masked.png)

4. After creating the Project Data Source, test the connection.  You should see the following:

![](https://github.com/andrzej-jedrzejewski/hive-jdbc-cloudera-jar/blob/master/images/data_source_conf_3_masked.png)

## How to Build
To build locally, you must have Maven installed and properly configured.  After that it's as simple as running `mvn:package`.  A file called `hive-jdbc-uber-x.jar` will be created in your `target` directory.  The newly created jar will have the Hive JDBC driver as well as all required dependencies.
