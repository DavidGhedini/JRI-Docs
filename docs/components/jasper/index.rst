
.. This is a comment. Note how any initial comments are moved by
   transforms to after the document title, subtitle, and docinfo.

.. demo.rst from: http://docutils.sourceforge.net/docs/user/rst/demo.txt

.. |EXAMPLE| image:: static/yi_jing_01_chien.jpg
   :width: 1em

**********************
Jasper
**********************

.. contents:: Table of Contents

JRI File Locations
==================

On installation, the JRI files are saved to::

   /home/tomcat/apache-tomcat-v/jasper_reports
   
Here, you will find the following::

   /home/tomcat/apache-tomcat-v/jasper_reports/conf
   
   /home/tomcat/apache-tomcat-v/jasper_reports/schedules
   
   /home/tomcat/apache-tomcat-v/jasper_reports/reports
   
   /home/tomcat/apache-tomcat-v/jasper_reports/logs
   
reports contains your Jasper report files.

conf contains the application.properties file

schedules contains the .sh files for the Scheduler


Gen Script
==========
The Tomcat init script is located under /etc/init.d/gen_jri_report.sh and has the contents below::



	#!/bin/bash -e

  source /etc/environment

  JRI_HOME="${CATALINA_HOME}/jasper_reports/"

  #source the report environment
  source "${JRI_HOME}/schedules/${1}_env.sh"

  DONT_MAIL="${2}"

  #set who is sending the mail
  export EMAIL='root@localhost'
  REPORT_FOLDER=$(dirname ${REP_ID})

  #encode the / in report id
  REP_ID=$(echo "${REP_ID}" | sed 's/\//%2F/g')

  if [ "${OPT_PARAMS}" ]; then
  OPT_PARAMS="&${OPT_PARAMS}"
  fi

  URL="http://localhost:8080/JasperReportsIntegration/report?_repName=${REP_ID}&_repFormat=${REP_FORMAT}&_dataSource=${REP_DATASOURCE}&_outFilename=${REP_FILE}${OPT_PARAMS}"

  TSTAMP=$(date '+%Y%m%d_%H%M%S')
  REP_FILEPATH="${JRI_HOME}/reports/${REPORT_FOLDER}/${TSTAMP}_${REP_FILE}"

  wget -O"${REP_FILEPATH}" "${URL}"
  if [ $? -ne 0 ]; then
  rm -f "${REP_FILEPATH}"
  fi






Version
=======

JRI Publisher has been tested with Tomcat 9.x
