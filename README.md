# **Application Name:** AutomationRequest

**Tool Objective:** Quickly send thousands of web requests using goroutines for multiple purposes.



The primary function house the command line parameters,

-l for a list of URLs/IPs,

-s for single

-n for the number of concurrent requests



I have also commented on the code with any notes and explanations. For the readfile function, it will read the full content of the file into memory. I found this to be better than using a buffered channel. It took quite a while, but I finally found the arguments for the http.transport that allows for insecure connections and out-of-date ciphers.



You may ask, why is this important for a security tool?

Let's say your internal red team at company X, and your job is to report all vulnerabilities. This past week, the F5-big IP RCE has dropped, and the business wants to know its effect. Most companies have pretty damn large networks, and I'm just speaking from an internal aspect. Typical, you'll see a 10.0.0.1/8, which is around 16 million hosts per subnet, and then any of those hosts can run this application on X number of ports. What I'm trying to paint for you is an actual photo. We'll first look at any release POC, and we'll quickly see it's using HTTPS on the standard port, with the path /tmui/login.JSP. With this in hand and our newly found goscript, we can quickly enumerate the company. We can now pull down each webserver by first trying to establish a connection. If any reports back within the parameters we set in the script, that will be printed out. From here, we can manually asset what we are dealing with.

#

**Why is this important, and what about OPSec?**

OPSecwouldn't matter here too much if I'm an internal red team and not under any operation.



**What if I wanted to stay low from the SOC and not drive up alerts/detection?**

Although it sounds obvious, I'll take my chances and hope the SOC doesn't have any on-prem or VPN data traffic metric going on. I have personally found these to be the third line in terms of alerts because of the false positives it may drive. Another side note: I have seen some SOC alerts that build up a heuristic profile on the domain user traffic size off VPN hours.



**Usefulness:**

- Checking any appliance/application on the network
- Checking for outdated applications
- Checking for default credentials in an automated style
- GoLang allows for cross-compilation



**Why is this tool important?**

The usefulness of this tool will help me when I am on assessments and need a way to quickly scan large networks for particular hosts that matches my criteria.



**Direction and Future Direction:**

I want to fix the protocol and port variables so they aren't statically set in the script. The script would be best if it was parsed from the argument. Some future direction includes modules that may consist of various other protocols, like DNS/FTP/SSH.
