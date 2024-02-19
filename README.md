# Firewall configuration


According to the OWASP (Open Web Application Security Project) injection attacks or OWASP injection attacks that include common cross-site scripting and SQL injection were the Number 1 Risk on the OWASP TOP 10 list in 2017 and 3rd in 2021.

What can we do to defend our web applications against these attacks? We can add a Web Application Firewall or WAF

What is an injection attack? 

It's when the threat actor has the ability to provide a malicious input to a web application usually through an input field that is not being coded to cater for input or validation that results in the web app executing unexpected or unwanted commands on the server hosting the web app. One of the most common injection attacks is SQL injection where the threat actor attempts to insert a SQL statement into a compromised input field attempting to query update or even worse delete the data from the database. Another common attack using this methodology is a command execution attack where a thread actor attempts to run multiple commands disguised as a single command which targets the underlying operating system attempting to retrieve information like usernames or unencrypted passwords or other details that may allow them to get an initial foothold on the system. 

Injection attacks can lead to various negative outcomes such as privilege escalation, data breaches, or denial of service.

WAF operates at layer 7 of the OSI model and monitors HTTP traffic between the web app and the internet, filtering out any potentially malicious requests by matching typical patterns described in its configured rules the pattern matching will look out for a combination of symbols and keywords that may represent a SQL statement or a shell command and block the communication before it executes on the server.

We update our Firewall:

![Screenshot 2024-02-19 at 12 30 26](https://github.com/redjules/Firewall-configuration/assets/106017493/59119661-295f-4845-8c82-ed3bcb89623d)

and install the os-nginx plugin - popular http server and reverse proxy:


![Screenshot 2024-02-19 at 12 32 04](https://github.com/redjules/Firewall-configuration/assets/106017493/238e2410-c2a0-420c-8fe9-f980c8ff8415)



