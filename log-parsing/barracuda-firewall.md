## Description
Barracuda Web Application Firewall is a security product provided by Barracuda.

https://campus.barracuda.com/product/webapplicationfirewall/doc/92767349/exporting-log-formats/

Barracuda Web Application Firewalls allow exporting in multiple different formats. In this example we will use its default log export method. Other formats may work with other parsers as well

## Example Log
**System Logs**
2014-05-20 00: 54:44.627 -0700  WAF1 SYS ADMIN_M ALER 51001 Account has been locked for user Kevin because the number of consecutive log-in failures exceeded the maximum allowed

| Parameters | Example Value |
| ---- | ---- |
| Time | 2014-05-20 00:54:44.627 -0700 |
| Unit Name | WAF1 |
| Log Type | SYS |
| Module Name | ADMIN_M |
| Log Level | ALER |
| Event ID | 51001 |
| Message | Account has been locked for user Kevin because the number of consecutive log-in failures exceeded the maximum allowed. |

**Web Firewall Log**
2014-04-11 10:50:30.411 +0530  wafbox1 WF ALER PRE_1_0_REQUEST 99.99.1.117 34006 99.99.109.2 80 global GLOBAL LOG NONE [POST /index.cgi] POST 99.99.109.2/index.cgi HTTP REQ-0+RES-0 "Mozilla/5.0 (X11; Linux i686; rv:12.0) Gecko/20100101 Firefox/12.0"  99.99.1.117 34005 Kevin http://99.99.109.2/index.cgi

| Parameters | Example Value |
| ---- | ---- |
| Time | 	2014-04-11 10:50:30.411 +0530 |
| Unit Name | wafbox1 |
| Log Type | WF |
| Severity | ALER |
| Attack Type | PRE_1_0_REQUEST |
| Client IP | 99.99.1.117 |
| Client Port | 34006 OR 43655 |
| Service IP  | 99.99.109.2 |
| Service Port | 80 |
| Rule | global |
| Rule Type | GLOBAL |
| Action | LOG |
| Follow-up Action | NONE |
| Attack Details | [POST /index.cgi] |
| Method | POST |
| Host + URL | 99.99.109.2/index.cgi OR 2001::1:109/index.cgi |
| Protocol | HTTP |
| Session ID | REQ-0+RES-0 |
| User Agent | Mozilla/5.0 (X11; Linux i686; rv:12.0) Gecko/20100101 Firefox/12.0 |
| Proxy IP | 99.99.1.117|
| Proxy Port | 34006 OR 43654 |
| Authenticated User | Kevin |
| Referrer | http://99.99.109.2/index.cgi OR http://2001:109/index.cgi |

**Access Log**
2014-04-11 12:04:04.735 +0530  wafbox1 TR 99.99.109.2 80 99.99.1.117 34065 "-" "-" GET HTTP 99.99.106.25 HTTP/1.1 200 2829 232 0 1127 10.11.25.117 80 21 REQ-0+RES-0  SERVER DEFAULT PASSIVE VALID /index.html name=srawat http://99.99.109.2/index.cgi namdksih=askdj "Mozilla/5.0 (X11; Linux i686; rv:12.0) Gecko/20100101 Firefox/12.0" 99.99.1.117 34065 John gzip,deflate 99.99.1.128 keep-alive

| Parameters | Example Value |
| ---- | ---- |
| Time | 	2014-04-11 12:04:04.735 +0530 |
| Unit Name | wafbox1 |
| Log Type | TR |
| Service IP | 99.99.109.2 |
| Service Port | 80 |
| Client IP | 99.99.1.117 |
| Client Port | 59589 |
| Login | - |
| Certificate user | - |
| Method | GET |
| Protocol | HTTP |
| Host | 99.99.106.25 |
| Version | HTTP/1.1 |
| HTTP Status | 200 |
| Bytes Sent | 2829 |
| Bytes Received | 232 |
| Cache Hit | 0 |
| Time Taken (ms) | 1127 |
| Server IP | 10.11.25.117 |
| Server Port | 80 |
| Server Time | 21 |
| Session ID | REQ-0+RES-0 |
| Response Type | SERVER |
| Profile Matched | DEFAULT |
| Protected | PASSIVE |
| WF Matched | VALID |
| URL | /index.html |
| Query String | name-srawat |
| Referrer | http://99.99.109.2/index.cgi |
| Cookie | namdksih=askdj |
| User Agent | Mozilla/5.0 (X11; Linux i686; rv:12.0) Gecko/20100101 Firefox/12.0 |
| Proxy IP | 99.99.1.117 |
| Proxy Port | 34065 |
| Authenticated User | John |
| Custom Header 1 | gzip, deflate |
| Custom Header 2 | 99.99.1.128 |
| Custom Header 3 | keep-alive |

## Example Parser
System Log
https://rubular.com/r/HSwdl8xiuNIQWs

Web Firewall Log
https://rubular.com/r/iLT7MRTlF2PgxD

Access Log
https://rubular.com/r/fK68YmfyGKjSRs
