# Web Application Firewall (WAF) configuration using NAXSI


According to the OWASP (Open Web Application Security Project) injection attacks or OWASP injection attacks that include common cross-site scripting and SQL injection were the Number 1 Risk on the OWASP TOP 10 list in 2017 and 3rd in 2021.

What can we do to defend our web applications against these attacks? We can add a Web Application Firewall or WAF

What is an injection attack? 

It's when the threat actor has the ability to provide a malicious input to a web application usually through an input field that is not being coded to cater for input or validation that results in the web app executing unexpected or unwanted commands on the server hosting the web app. One of the most common injection attacks is SQL injection where the threat actor attempts to insert a SQL statement into a compromised input field attempting to query update or even worse delete the data from the database. Another common attack using this methodology is a command execution attack where a thread actor attempts to run multiple commands disguised as a single command which targets the underlying operating system attempting to retrieve information like usernames or unencrypted passwords or other details that may allow them to get an initial foothold on the system. 

Injection attacks can lead to various negative outcomes such as privilege escalation, data breaches, or denial of service.

WAF operates at layer 7 of the OSI model and monitors HTTP traffic between the web app and the internet, filtering out any potentially malicious requests by matching typical patterns described in its configured rules the pattern matching will look out for a combination of symbols and keywords that may represent a SQL statement or a shell command and block the communication before it executes on the server.


![Screenshot 2024-02-19 at 17 49 01](https://github.com/redjules/Firewall-configuration/assets/106017493/2430a49c-a2a8-4754-9a82-9af772f22b33)


We update our Firewall:

![Screenshot 2024-02-19 at 12 30 26](https://github.com/redjules/Firewall-configuration/assets/106017493/59119661-295f-4845-8c82-ed3bcb89623d)

and install the os-nginx plugin - popular http server and reverse proxy:


![Screenshot 2024-02-19 at 12 32 04](https://github.com/redjules/Firewall-configuration/assets/106017493/238e2410-c2a0-420c-8fe9-f980c8ff8415)

![Screenshot 2024-02-19 at 17 28 18](https://github.com/redjules/Firewall-configuration/assets/106017493/373e5c68-dd17-4988-89bb-fcef820d2457)

![Screenshot 2024-02-19 at 17 29 18](https://github.com/redjules/Firewall-configuration/assets/106017493/3557d7fc-51c5-4f2a-b7cd-e8e3a1a00ffd)

![Screenshot 2024-02-19 at 17 30 08](https://github.com/redjules/Firewall-configuration/assets/106017493/a73d2e4c-62b3-4f41-bfc4-59d38442b09e)

![Screenshot 2024-02-19 at 17 30 37](https://github.com/redjules/Firewall-configuration/assets/106017493/7dbd4a8a-b19f-4f14-a1ba-b6437003c94f)

![Screenshot 2024-02-19 at 17 30 57](https://github.com/redjules/Firewall-configuration/assets/106017493/46735678-51dd-401a-a89d-47b8af50c0e2)

![Screenshot 2024-02-19 at 17 31 08](https://github.com/redjules/Firewall-configuration/assets/106017493/b00d07af-6f07-4139-bec6-7a62a0274478)

![Screenshot 2024-02-19 at 17 31 32](https://github.com/redjules/Firewall-configuration/assets/106017493/4382b76c-a231-4b92-9a10-e85f42f70443)

![Screenshot 2024-02-19 at 17 31 55](https://github.com/redjules/Firewall-configuration/assets/106017493/59790582-2224-413f-b504-3da68543e231)

![Screenshot 2024-02-19 at 17 32 29](https://github.com/redjules/Firewall-configuration/assets/106017493/80fdc992-91c9-46ff-87d7-89ccc4d42d87)

![Screenshot 2024-02-19 at 17 32 51](https://github.com/redjules/Firewall-configuration/assets/106017493/7716f66f-fc32-416d-84bf-33988a2fa4a5)

![Screenshot 2024-02-19 at 17 33 51](https://github.com/redjules/Firewall-configuration/assets/106017493/d2b4aacb-669f-4a04-9117-0f9bcfd3bc0d)

![Screenshot 2024-02-19 at 17 34 06](https://github.com/redjules/Firewall-configuration/assets/106017493/26df8acd-ef52-4673-a5d6-f63bc009b6bf)

![Screenshot 2024-02-19 at 17 34 52](https://github.com/redjules/Firewall-configuration/assets/106017493/17fa549f-fa3a-4bea-9e25-32fb8fe15a6a)

![Screenshot 2024-02-19 at 17 35 16](https://github.com/redjules/Firewall-configuration/assets/106017493/49fd8e3b-65af-4d7c-98a3-9b3d309bce51)

![Screenshot 2024-02-19 at 17 35 40](https://github.com/redjules/Firewall-configuration/assets/106017493/2a16ad49-09e1-42b5-8b9b-59037e958ee0)

This is a web app to practice penetration testing. To see the WAF in action, we will simulate a popular SQL injection attack:

![Screenshot 2024-02-19 at 17 38 56](https://github.com/redjules/Firewall-configuration/assets/106017493/d6e206e0-35ed-4c23-81cb-9961ba1361ec)

When we submit, we get all the names from the user database

![Screenshot 2024-02-19 at 17 39 34](https://github.com/redjules/Firewall-configuration/assets/106017493/fcf7f027-ceea-418a-9169-45a2223e0d95)

Another attack is the command injection attack:

![Screenshot 2024-02-19 at 17 41 11](https://github.com/redjules/Firewall-configuration/assets/106017493/883e011c-5296-413d-884d-aa98b87adceb)

We submit and we get old active user accounts:

![Screenshot 2024-02-19 at 17 42 11](https://github.com/redjules/Firewall-configuration/assets/106017493/b25e02ea-b831-46a4-b668-0aa12af0791d)

Now the attacker has an idea which accounts are active on the server and try to exploit these individual accounts to try to get a foothold on the server


we disable Learning mode from the firewall:

![Screenshot 2024-02-19 at 17 44 33](https://github.com/redjules/Firewall-configuration/assets/106017493/8f62dcae-f574-40b8-9819-3cf19a83dd97)

we apply the changes:

![Screenshot 2024-02-19 at 17 44 51](https://github.com/redjules/Firewall-configuration/assets/106017493/9e5d2eb6-be80-4d4d-9a74-0703fe78531c)


we try the SQL injection attack again:

![Screenshot 2024-02-19 at 17 36 43](https://github.com/redjules/Firewall-configuration/assets/106017493/4bef6211-ba99-4a40-9779-61a64cdd6400)

and we get an error message from OPNsense which says that our request has been denied due to security reasons by the WAF:

![Screenshot 2024-02-19 at 17 45 53](https://github.com/redjules/Firewall-configuration/assets/106017493/b0913eeb-28d5-4dc9-b0ff-75b2cb94ac26)

we try the Command Injection attack again:

![Screenshot 2024-02-19 at 17 47 16](https://github.com/redjules/Firewall-configuration/assets/106017493/9a04f36c-0c7d-4b19-98da-aaeec4a61edb)

and same error message:

![Screenshot 2024-02-19 at 17 47 48](https://github.com/redjules/Firewall-configuration/assets/106017493/719ccf17-cafa-4482-af6b-bb992b07e6b9)



