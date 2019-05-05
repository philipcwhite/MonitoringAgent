# Monitoring Agent 1.0.3

This project is no longer supported. I have shifted all efforts to the new Monitoring server written in Python. Thanks to everyone who took the time to check out this project.

This is a VB.Net Windows Service WMI Monitoring Agent

This is a basic Windows monitoring agent that collects system, processor, memory, disk, and service data, and sends the data to a central server. It works in conjuntion with the Monitoring Server application.

### Changes for Version 1.0.3 (2018/02/23):

1.  Added Network Monitoring  

### Changes for Version 1.0.2 (2017/02/12):

1.  Added an uptime monitor and changed the polling period back to 1 minute.  


### Changes for Version 1.0.1 (2017/01/21):

1.  Fixed IPv4 issue found in Windows 10.


### Changes for Version 1.0.0 (2016/02/06):

1.  Changed installation directory to pcwsoft.

2.  Added NOTICE file.


### Changes for Version 1.0.0 (2016/02/06):

1.  Changed installation directory to pcwsoft.

2.  Added NOTICE file.


### Changes for Version 2.5.0 (2016/01/26):

1.  Updated hostname to use uppercase NetBIOS name instead of FQDN.  This could potentially be a problem for companies who use the same name with different domains.  

### Changes for Version 2.5.0 (2016/01/18):

1.  Added GZip compression.  Network packets are now aproximately 1/10th the size as previous.  

2.  Changed Services to monitor all Auto services by default.  No configuration required.

3.  Updated configuration file to remove uncesessary items.


### Changes for Version 2.3.5 (2016/01/15):

1.  Implemented SSL using TLS 1.2.  This is still not the most secure due to fact that I am not verifying certificates and the agent does not require a certificate.  We are just accepting anything.  You can use your own server cert with the Monitoring Server.  I will make an option later to verify the cert.  I switched from custom encryption to this incase I build a linux agent later or someone else decides to.  The TCP server should accept any valid TLS 1.2 connections.  The new default behavior of the agent and the server is to use non-encrypted TCP connections.  It's faster, lower overhead, and this is monitoring data which despite what some say, is not sensitive data.  If you are using the agent or monitoring server you must upgrade to use this.  

2.  I will most likely be updating the build numbers to match the monitoring server as we get closer to a production release.  Also I do still plan to make an option for the agent to send data to itself.  This will let you do whatever you want with the agent.   


### Changes for Version 2.2.5 (2016/01/04):

1.  Added Monitors for Pagefile and Logical Disk Performance.  Removed MB Free.


### Changes for Version 2.2.5 (2015/12/31):

1.  Set agent to run at 5 minute intervals based on system time.  So the agent will run at 00,05,10,15 mins etc.  This was done to comply with graphing on the server side which is coming soon.  
 

### Changes for Version 2.2.0 (2015/12/27):

This is the most significant change to the agent to date.  The agent now runs in memory and does not write the database to disk.  I will add some debugging to re-enable writing data to disk at a later time.  Something like send to self.  TCP Receive was not currently being used so I removed it for security reasons.

1.  Removed TCP receive, Agent Database

2.  Updated XML packets to provide a cleaner more consistant packet.  

3.  Failed data is no longer resent

4.  Performance has improved significantly especially on the server side.  


### Changes for Version 2.1.0 (2015/12/21):

1.  Fixed bug closing network stream. 

2.  Changed configuration to remove instance and rewrote parameter as property.  Please use the latest Version of the server app as well to insure compatibility.

3.  Changed CPU collection to use Preformatted WMI data.

4.  Set several default service parameters.  This will most likely be refined in a future update.

## Changes for Version 2.0.6 (2015/12/20):

1.  Set installer to 64bit default.


### Changes for Version 2.0.4 (2015/12/04):

1.  Fixed an issue where the CPU was reporting a negative value.

Changes for Version 2.0.3 (2015/11/30):

1.  Added code to abort threads on service stop.


### Changes for Version 2.0.2 (2015/11/29):

1.  Changed Default TCP Send port to 10001.


### Changes for Version 2.0.1 (2015/11/26):

1. TCP connections now error correctly

2. Data that is not sent due to TCP errors will be sent when the connection is reestablished


### Changes for Version 2.0.0 (2015/11/24):

1. TCP connections now use asynchronous communication.

2. TCP logging has been enabled by default.

3. Most of the Public subroutines were converted from shared to instances.

4. Installation path has changed.


Application Installer:

This Agent uses the Visual Studio installer. It will install the Agent by default to C:\Program Files\wcpSoft\MonitoringAgent. This can be changed during setup. The agent is also by default set to Automatic startup and runs under the local system account.

Configuration and Data files:

AgentConfiguration.xml is the Agent configuration. It is also created when the agent is started.

To configure services add a new line with the following values.

object class="windows" property="service" value="ServiceName"

Network Information:

This application sends data over TCP port 10000 by default. This values can be changed in the AgentConfiguration.xml file.

Security/Encryption:

This aplication uses a weak version of AES packet encryption over TCP. Please change the Key and IV if you plan on using this code for production.

About the Author:

My name is Phil White and I have been working with enterprise system monitoring solutions for over 9 years. I enjoy learning new technology, writing code, and playing guitar in my free time. I hope you find my applications useful. 
