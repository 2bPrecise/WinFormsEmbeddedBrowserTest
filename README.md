# WinFormsEmbeddedBrowserTest
Microsoft issue example - WinFormsEmbeddedBrowserTest

Simple WinForm application with WebBrowser control embedding web application.
This is a showcase for Microsoft to work on issue with detailed provided below:

PROBLEM
•       Web application hosted in WinForms webBrowser control failed to render because one of the internal dependencies tries to access Intl API.
•       Steps to reproduce 
o   Use any of the following machines for testing: Win8.1+IE11 / Windows Server 2012 R2 + IE11
o   Install the following update: kb4489881
o   Reboot the machine
o   Create a simple WinForms application and navigate to any website trying to access Intl API our case was testing if Intl.v8BreakIterator is defined
The actual piece of code that triggers the issue:
const hasV8BreakIterator = (typeof Intl !== 'undefined' && (Intl as any).v8BreakIterator);
o   You would get the following error: "typeError: intl is not available"
o   Uninstall kb4489881
o   Reboot the machine
o   Run the same steps again, you will get no errors.
•       What have you tried so far
o   Exactly what listed in the steps to reproduce, the only resolution we found is to uninstall the kb4489881 update. 
o   After removing the KB our system got back to normal   
 
O/S AND PRODUCT DETAIL 
•       O/S Version 
o   Windows Server 2012 R2 / Windows 8.1 x64
•       O/S Service Pack 
o   None
•       O/S Language   
o   En-US
•       Microsoft Product Version/Service Pack        
o   Windows 8.1 Enterprise Evaluation
o   Windows Server 2012 (No SP)
 
Severity (I strongly recommend not to make this a Sev A if you don’t have customers who are down. Sev A means you are working 24x7 with us)
•       (A) Critical Situation (CritSit): impact to production systems with no workarounds. 
•       (B) Premier (2 hour target response time) 
•       (C) - Premier (4 hour target response time)
 
BUSINESS IMPACT (this is espeically needed if you are opening  a Sev A case)
•       Business Impact
o   System wide outage on our customers ends. 
Users cannot access our application at all, Physicians, Nurses, etc. system wide crash.  
Customers consider this outage as Patient Safety issue  (considered HIPAA violation)    
•       # of users impacted – 20000+
•       # of machines impacted – 206       
