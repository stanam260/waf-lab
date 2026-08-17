**What is a WAF?**

A Web Application Firewall (WAF) is a security tool that protects web applications by monitoring, filtering, and blocking malicious HTTP/HTTPS traffic between clients and the web application.**

**What are the HTTP headers?**

HTTP headers contain additional information sent by a client to a web server as part of an HTTP request.

**Structure of the HTTP headers** 

Every header has the following format   

<img width="905" height="207" alt="waf1" src="https://github.com/user-attachments/assets/7e763fdd-97e7-4d08-8728-20604b13ddad" />

**HTTP Request Headers**

The following example shows some of the headers included in an HTTP POST request. Each header consists of a name and its corresponding value.

<img width="1304" height="706" alt="waf2" src="https://github.com/user-attachments/assets/63bce221-d4f9-41c8-ac2c-bce52b867c54" />


**Host:** Identifies the domain and optional port of the web server the client wants to access

**User-Agent:** Identifies the client software making the request, such as the browser and its version.

**Content-Length:** Indicates the size, in bytes, of the request body sent to the server.

**Accept-Encoding:** Specifies the compression formats the client supports, such as  gzip or  br.

**Cookie:** Contains data sent by the browser to help the server remember session information and user preferences.

**HTTP Response Headers**

The following screenshot shows some of the headers returned by the server in an HTTP response.

<img width="1488" height="332" alt="waf3 a la(s) 11 47 07 a m" src="https://github.com/user-attachments/assets/351d3fb5-86c8-4b7a-9470-1b5651bf6677" />

**Content-Type:** Specifies the format of the response body so the client knows how to interpret and display it.

An HTTP response can also include additional headers such as:

**Set-Cookie:** Requests that the browser save information that may be included in later requests.

**Cache-Control:** Provides instructions about whether the response can be cached and when it should be retrieved again.

**Content-Encoding:** Indicates whether the response body was compressed or encoded before transmission.

**SQL Injection Test**
 
After reviewing the purpose of a WAF and the structure of HTTP requests and headers, this lab tests a basic rule designed to detect and block SQL injection attempts.

The screenshot shows a SQL injection payload entered into the email field. It attempts to bypass authentication and log in without valid credentials.
<img width="1486" height="724" alt="waf4" src="https://github.com/user-attachments/assets/b9daa007-964b-4296-918a-43a15b569afb" />

After submitting the SQL injection payload, the application bypasses authentication and grants access to the administrator account.

<img width="1443" height="757" alt="waf5" src="https://github.com/user-attachments/assets/6497eed5-62bb-47ce-a353-62298aef3671" />


A WAF rule was configured in the  rules.conf  file to detect a basic SQL injection pattern

<img width="1489" height="152" alt="waf6" src="https://github.com/user-attachments/assets/cf5a4ece-5b0d-4b66-87c7-e351ca84526b" />

Note : DetectionOnly mode is used to test WAF rules, review alerts, and identify false positives without blocking requests. After validating the rule, blocking mode can be enabled.

MODSEC_RULE_ENGINE was set to  on  to enable blocking mode, allowing the WAF to block malicious requests.

<img width="1473" height="319" alt="waf7" src="https://github.com/user-attachments/assets/37cb240f-570e-494c-92ca-7d9eaba9d64e" />


After enabling the rule in blocking mode, the WAF blocked the SQL injection and returned a 403 Forbidden response, preventing the admin login.
<img width="1413" height="761" alt="waf8" src="https://github.com/user-attachments/assets/550de489-a645-4413-8042-4571124580ab" />
