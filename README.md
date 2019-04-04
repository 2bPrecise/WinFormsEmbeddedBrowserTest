# WinFormsEmbeddedBrowserTest
Microsoft issue example - WinFormsEmbeddedBrowserTest

Simple WinForm application with WebBrowser control embedding web application.
This is a showcase for Microsoft to work on issue with detailed provided below:

* PROBLEM
    * Web application hosted in WinForms webBrowser control failed to render because one of the internal dependencies tries to access Intl API.
* Steps to reproduce 
    * Use any of the following machines for testing: Win8.1+IE11 / Windows Server 2012 R2 + IE11
    * Install the following update: kb4489881
    * Reboot the machine
    * Create a simple WinForms application and navigate to any website trying to access Intl API our case was testing if Intl.v8BreakIterator is defined
The actual piece of code that triggers the issue:
`const hasV8BreakIterator = (typeof Intl !== 'undefined' && (Intl as any).v8BreakIterator);`
    * You would get the following error: "typeError: intl is not available"
    * Uninstall kb4489881
    * Reboot the machine
    * Run the same steps again, you will get no errors.
* What have you tried so far
    * Exactly what listed in the steps to reproduce, the only resolution we found is to uninstall the kb4489881 update. 
    * After removing the KB our system got back to normal   
 
* O/S AND PRODUCT DETAIL 
    * O/S Version 
        * Windows Server 2012 R2 / Windows 8.1 x64   
    * O/S Service Pack 
        *   None
    * O/S Language   
        * En-US
    * Microsoft Product Version/Service Pack        
        * Windows 8.1 Enterprise Evaluation
        * Windows Server 2012 (No SP) 

# Info
* Microsoft Update the casued the issue: https://support.microsoft.com/en-us/help/4489881/windows-8-1-update-kb4489881
