# Get-DAGHealth.ps1
Exchange Server 2010/2013 Database Availability Group health check script

Performs a series of health checks on the Database Availability Groups
and outputs the results to screen or HTML email.

## Parameters

* -Detailed, When this parameter is used a more detailed report is shown in the output.
* -HTMLFile, When this parameter is used the HTML report is also writte to a file.
* -SendEmail, Sends the HTML report via email using the SMTP configuration within the Settings.xml file.
* -Monitoring, This parameter can be used to integrate this script as check into a monitoring system like Nagios/Icinga and Check_MK.

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

## Monitoring

This script can be used as check via the [Check_MK_Agent](https://mathias-kettner.de/checkmk_windows.html). Check out the Monitoring settings in the [Settings.xml](/Settings.xml) file.

See [Check_MK local checks](https://mathias-kettner.de/checkmk_localchecks.html) for more information.

### Via the Agent
Save the following batch script under `C:\Program Files (x86)\check_mk\local`:

```dosbatch
@echo off

rem C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe -noexit -command ". 'C:\Program Files\Microsoft\Exchange Server\V15\bin\RemoteExchange.ps1'; Connect-ExchangeServer -auto -ClientApplication:ManagementShell; . 'C:\Program Files (x86)\check_mk\more\DAG_production\get-daghealth.ps1'"

c:\windows\system32\WindowsPowerShell\v1.0\powershell.exe -File "C:\Program Files (x86)\check_mk\Powershell\DAG\get-daghealth.ps1"
```

Unfortunately, I could not get this to work. "WARNING: No snap-ins have been registered for Windows PowerShell version 4."

### Via task scheduler

Create a task to run lets say every hour.

Then save this script into the file `C:\Program Files (x86)\check_mk\local\dagmon.bat`:
```dosbatch
@echo off

rem See Task Scheduler
type c:\tmp\dag_state.txt
```

You might need to create or change the directory: c:\tmp

## More information:
http://exchangeserverpro.com/get-daghealth-ps1-database-availability-group-health-check-script/

## Credits
Written by: Paul Cunningham

Find me on:

* My Blog:	http://paulcunningham.me
* Twitter:	https://twitter.com/paulcunningham
* LinkedIn:	http://au.linkedin.com/in/cunninghamp/
* Github:	https://github.com/cunninghamp

Support to use this script in Monitoring was added by Robin `ypid` Schneider.

Find me on:

* My homepage: http://ypid.de/
* GitHub: https://github.com/ypid

For more Exchange Server tips, tricks and news check out Exchange Server Pro.

* Website:	http://exchangeserverpro.com
* Twitter:	http://twitter.com/exchservpro
