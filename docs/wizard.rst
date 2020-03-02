.. _wizard-label:
************
Wizard
************

Once the module is installed, the Wizrd is used to configure the components.

Go to Servers > JRI Publisher:

.. image:: _static/3.png

The main Wizard screen will then display each step.

While most steps are self-explanatory, we will cover Tomcat, JDK, and JRI selection below:

.. image:: _static/4-java.png

Select the JDK you wish to use.  We have tested with JDK 8

.. image:: _static/5-java.png


With JDK selected, select Tomcat version below.  

.. image:: _static/8-tomcat.png

We have test with Tomcat 9.x:

.. image:: _static/9-tomcat.png


With Tomcat installed, select JRI version below.  

.. image:: _static/13-jri.png

We have tested with 2.4.0:

.. image:: _static/14-jri.png

If you wish to use a Beta version of JRI, tick the "Show Beta Versions" box:  

.. image:: _static/15-jri.png

Once each step of the Wizard is completed, the Wizard can be removed:

.. image:: _static/19-donei.png

With the Wizard completed, your module should appear as below:

.. image:: _static/21-Start-Tomcat.png



.. note::
    The JRI application is not deployed at this point.  You need to Start Tomcat
    in order to deploy it.  Do so before any further operations as it is required
    in order to write configuration files, etc...
    

About Haveged
===================

Haveged is an entropy generator that will provide markedly faster JVM startup times.
The caveat is that it will use much higher CPU load (although for shorter duration due
to decreased JVM start up time).  Bear this in mind if deploying on VM with limited CPU
or other critical applications.

