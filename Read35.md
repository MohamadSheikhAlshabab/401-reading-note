# Topic [URL](https://github.com/MohamadSheikhAlshabab/401-reading-note/blob/master/Read35.md)

## Web application security

  - __Web application security__:
    - is a branch of information security that deals specifically with security of websites, web applications and web services.
    - At a high level, web application security draws on the principles of application security but applies them specifically to internet and web systems.
  
  - __Security threats__:
    - The majority of web application attacks occur through cross-site scripting (XSS) and SQL injection attacks which typically are made possible by flawed coding and failure to sanitize application inputs and outputs.
    - These attacks are ranked in the 2009 CWE/SANS Top 25 Most Dangerous Programming Errors.
    
  - __The Open Web Application Security Project (OWASP)__
    - provides free and open resources. 
    - It is led by a non-profit called The OWASP Foundation. 
    - The OWASP Top 10 - 2017 is the published result of recent research based on comprehensive data compiled from over 40 partner organizations.
    - From this data, approximately 2.3 million vulnerabilities were discovered across over 50,000 applications.
    
    - the ten most critical web application security risks include:
      - Injection
      - Broken authentication
      - Sensitive data exposure
      - XML external entities (XXE)
      - Broken access control      
      - Security misconfiguration
      - Cross-site scripting (XSS)
      - Insecure deserialization
      - Using components with known vulnerabilities
      - Insufficient logging and monitoring
      
---
## Security in Django

  - __Cross site scripting (XSS) protection__:
    - XSS attacks allow a user to inject client side scripts into the browsers of other users.
    - This is usually achieved by storing the malicious scripts in the database where it will be retrieved and displayed to other users, or by getting users to click a link which will cause the attacker’s JavaScript to be executed by the user’s browser. However, XSS attacks can originate from any untrusted source of data, such as cookies or Web services, whenever the data is not sufficiently sanitized before including in a page.
    - Using Django templates protects you against the majority of XSS attacks.
    - However, it is important to understand what protections it provides and its limitations.
    
  - __Cross site request forgery (CSRF) protection__:
    - CSRF attacks allow a malicious user to execute actions using the credentials of another user without that user’s knowledge or consent.  
    - Django has built-in protection against most types of CSRF attacks, providing you have enabled and used it where appropriate. However, as with any mitigation technique, there are limitations.
    - For example, it is possible to disable the CSRF module globally or for particular views.
    - You should only do this if you know what you are doing. 
    - There are other limitations if your site has subdomains that are outside of your control.
    - CSRF protection works by checking for a secret in each POST request.
    
- __SQL injection protection__:
  - SQL injection is a type of attack where a malicious user is able to execute arbitrary SQL code on a database.
  - This can result in records being deleted or data leakage.
  - Django’s querysets are protected from SQL injection since their queries are constructed using query parameterization.
  - A query’s SQL code is defined separately from the query’s parameters.
  - Since parameters may be user-provided and therefore unsafe, they are escaped by the underlying database driver.
  - Django also gives developers power to write raw queries or execute custom sql.
  - These capabilities should be used sparingly and you should always be careful to properly escape any parameters that the user can control.
  - In addition, you should exercise caution when using extra() and RawSQL.

- __Clickjacking protection__:
  - Clickjacking is a type of attack where a malicious site wraps another site in a frame. 
  - This attack can result in an unsuspecting user being tricked into performing unintended actions on the target site. 
  
- __SSL/HTTPS__
  - It is always better for security to deploy your site behind HTTPS.
  - Without this, it is possible for malicious network users to sniff authentication credentials or any other information transferred between client and server, and in some cases – active network attackers – to alter data that is sent in either direction. 
  
- __Host header validation__
  - Django uses the Host header provided by the client to construct URLs in certain cases.
  - While these values are sanitized to prevent Cross Site Scripting attacks, a fake Host value can be used for Cross-Site Request Forgery, cache poisoning attacks, and poisoning links in emails.
  
- __Referrer policy__
  - Browsers use the Referer header as a way to send information to a site about how users got there.
  - By setting a Referrer Policy you can help to protect the privacy of your users, restricting under which circumstances the Referer header is set.
  
- __Session security__:
  - Similar to the CSRF limitations requiring a site to be deployed such that untrusted users don’t have access to any subdomains, django.contrib.sessions also has limitations.
    
