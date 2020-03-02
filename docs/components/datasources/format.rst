.. This is a comment. Note how any initial comments are moved by
   transforms to after the document title, subtitle, and docinfo.

.. demo.rst from: http://docutils.sourceforge.net/docs/user/rst/demo.txt

.. |EXAMPLE| image:: static/yi_jing_01_chien.jpg
   :width: 1em

**********************
Data Sources
**********************

.. contents:: Table of Contents
Types
=====

Data Sources are used to connect your Oracle database.

JRI Publisher supports both JDBC and JNDI Data Source types included with JRI.

JDBC Data Sources are stored in a flat file at::

   /home/tomcat/apache-tomcat-v/jasper_reports/conf/
   
DBC Data Sources have the following form::

   #====================================================================
   # JDBC datasource configuration
   # http://www.orafaq.com/wiki/JDBC#Thin_driver
   # additional jdbc configurations, please uncomment
   #====================================================================
   [datasource:test]
   name=test
   url=jdbc:oracle:thin:@127.0.0.1:1521:XE
   username=my_oracle_user
   password=my_oracle_user_pwd

JNDI Data Sources are stored in a database and referenced in the application server rather than stored in a flat file as with JDBC Data Sources.

JNDI Data Sources have the following form::

   #====================================================================
   # Native JNDI datasource, to be configured in the application server
   # name: jndi_test
   #====================================================================
   [datasource:jndi_test]
   type=jndi
   name=jndi_test



