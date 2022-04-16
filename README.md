# Week 7 & 8 Project: WordPress vs. Kali


1. XSS: 
- steps: Create a post with ```<svg onload=alert(1)>``` in it. We need this for the user to get the alert when they comment later once the post is published.
When the post is published, the user can go to the published website by either going to a public or a private one. 
When visiting the public website where the post includes XSS script, user can comment ```<svg onload=alert(1)>``` to actually run the script itself to get the alert on their web broswer.

- types of vulnerabilities: XSS Script can be run when commenting on a post that includes that script.
- CVE identifiers:
- affected versions and patches:
 | [!] Title: WordPress <= 4.1.1 - Unauthenticated Stored Cross-Site Scripting (XSS)
 |     Fixed in: 4.1.2
 |     References:
 |      - https://wpscan.com/vulnerability/604b553d-5492-4f8c-af7a-db7169780032
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2015-3438
 |      - https://wordpress.org/news/2015/04/wordpress-4-1-2/
 |      - https://cedricvb.be/post/wordpress-stored-xss-vulnerability-4-1-2/
- source code:
- screen cap: 

2. SQLI
- steps:
- types of vulnerabilities:
- CVE identifiers:
- affected versions and patches
- source code:
- screen cap:


3. CSRF
- steps: First we get the script that will alert the user of the cookie information.
Then we include this script when creating a post. Then, when we visit that post, we can see that the alert doesn't appear (since we haven't added it in the "text" part -- the source code won't read it). However, we can still run that script by commenting the same script in one of the comments. 
We can also run this alert by updating the "text" of the post. Then when we view the page, the alert immediately pops up.
- types of vulnerabilities: shows cookie details when adding scripts to a post, commenting on a post, and updating a post
- CVE identifiers:
- affected versions and patches:
- [!] Title: WordPress 2.8-4.7 - Accessibility Mode Cross-Site Request Forgery (CSRF)
 |     Fixed in: 4.1.14
 |     References:
 |      - https://wpscan.com/vulnerability/e080c934-6a98-4726-8e7a-43a718d05e79
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5492
 |      - https://github.com/WordPress/WordPress/commit/03e5c0314aeffe6b27f4b98fef842bf0fb00c733
 |      - https://wordpress.org/news/2017/01/wordpress-4-7-1-security-and-maintenance-release/
- source code:
- screen cap:


4. User Enumeration
- steps: (1) When logging into Wordpress, we can see that when we input an existing username, we get an ERROR message saying that there is a user with that name. 

(2) When WPScanning for usernames, we can see a list of all registered usernames including all types of users (admin, contributor, subscriber). WPSCan indicates that it has found this through the same login failed error message that shows when one logs in with a username that already exists. 
(3) When WPScanning for passwords, we can see that login attempts made by the usernames from username and passwords.txt files worked. 
- types of vulnerabilities: We can identify usernames with wpscan. We can check login attempts by WPScan.
- CVE identifiers: 
- affected versions and patches: WordPress version 4.1 identified (Insecure, released on 2014-12-18).
 | Found By: Rss Generator (Passive Detection)
 |  - http://127.0.0.1:8080/?feed=rss2, <generator>http://wordpress.org/?v=4.1</generator>
 |  - http://127.0.0.1:8080/?feed=comments-rss2, <generator>http://wordpress.org/?v=4.1</generator>

- source code: 
- screen cap: 
Username Vulnerability:
![](https://github.com/hoonman/cybersecurity_week7_8/blob/main/usernameVulnerability.gif)
Password Vulnerability: 
![](https://github.com/hoonman/cybersecurity_week7_8/blob/main/passwordVulnerability.gif)

5. Privilege Escalation
- steps: Search for a private post by manipulating the URL of a 
- types of vulnerabilities: When being admin, we can view a private post by manipulating the URL.
- CVE identifiers:
- affected versions and patches:
- source code:
- screen cap:
![](https://github.com/hoonman/cybersecurity_week7_8/blob/main/urlManip.gif)
