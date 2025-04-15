<h1>Graylog</h1>

 
<h2>Description</h2>
Graylog is a leading centralized log management solution built to open standards for capturing, storing, and enabling real-time analysis of terabytes of machine data
<br />


<h2>Languages and Utilities Used</h2>

- <b>Graylog</b> 


<h2>Environments Used </h2>

- <b>Centos 7  </b>

<h2>Tooling Walkthrough:</h2>

<p align="center">
Steps to configure your linux clients to send syslog information to Graylog
<br />
<br />
   <p align="left">
1. add port or ports to the firewall<br />
  <br />
  -	a. firewall-cmd --zone public --add-port 5140/udp --permanent
  <br />
  - b. firewall-cmd --reload
<br/>
<br/>
2. now that Graylog is accepting syslog information, we need to configure our clients to send the information. To do that, SSH into a different Linux server (one you want to have send syslog details to Graylog) and create a new rsyslog configuration file<br />
<br />
- a. vi /etc/rsyslog.d/90-graylog.conf<br />
 <br />
- b. in that file, paste the following:
	  *.* @{GRAYLOG_SERVER_IP_ADDRESS}:5140;RSYSLOG_SyslogProtocol23Format
	where SERVER is the IP address of your Graylog server.
*.* @10.1.30.51:5140;RSYSLOG_SyslogProtocol23Format<br />
<br />
<br />
3. systemctl restart rsyslog



<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
