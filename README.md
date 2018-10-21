# Get-DAGHealth.ps1
Exchange Server 2010/2013 Database Availability Group health check script

Performs a series of health checks on the Database Availability Groups
and outputs the results to screen or HTML email.

## Parameters

* -Detailed, When this parameter is used a more detailed report is shown in the output.
* -HTMLFile, When this parameter is used the HTML report is also writte to a file.
* -SendEmail, Sends the HTML report via email using the SMTP configuration within the Settings.xml file.

## Examples
```
.\Get-DAGHealth.ps1
```
Checks all DAGs in the organization and outputs a health summary to the PowerShell window.

```
.\Get-DAGHealth.ps1 -Detailed
```
Checks all DAGs in the organization and outputs a detailed health report to the PowerShell
window. Due to the amount of detail the full report may get cut off in your window. I recommend
detailed reports be output to HTML file or email instead.

```
.\Get-DAGHealth.ps1 -Detailed -SendEmail
```
Checks all DAGs in the organization and outputs a detailed health report via email using
the SMTP settings you configure in the script.

## More information:
http://exchangeserverpro.com/get-daghealth-ps1-database-availability-group-health-check-script/

## Credits
Written by: Paul Cunningham

Find me on:

* My Blog:	https://paulcunningham.me
* Twitter:	https://twitter.com/paulcunningham
* LinkedIn:	https://au.linkedin.com/in/cunninghamp/
* Github:	https://github.com/cunninghamp

Check out my [books](https://paulcunningham.me/books/) and [courses](https://paulcunningham.me/training/) to learn more about Office 365 and Exchange Server.
