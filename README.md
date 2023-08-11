# MDT-SCRipts

```
### Bootstrap.ini

[Settings]
Priority=Default

[Default]
DeployRoot=\\DC1\DeploymentShare$

UserID=Administrator
UserDomain=kevinmylab.com  #Notreally needed
UserPassword=Pass
KeyboardLocale=en-US
SkipBDDWelcome=YES

```
```
### CustomSettings.ini
[Settings]
Priority=Default
Properties=MyCustomProperty

[Default]

SkipTaskSequence=YES
TaskSequenceID=WIN
SkipComputerName=YES

SkipDomainMembership=YES
DomainAdmin=serviceaccount # All the domain stuff not needed if you plan on using the Powershell script to join the domain. Add it to the tasksequence
DomainAdminDomain=domain.local
DomainAdminPassword=pass
JoinDomain=domain.local
AdminPassword=pass

_SMSTSORGNAME=Kevinmylab Corp
_SMSTSpackageName=%TaskSequenceName%

OSInstall=Y
SkipCapture=YES
SkipAdminPassword=YES
SkipProductKey=YES
SkipComputerBackup=YES
SkipBitLocker=YES
SkipBDDWelcome=YES
SkipUserData=YES
SkipSummary=YES
SkipFinalSummary=YES
SkipTimeZone=YES
TimeZoneName=Eastern Standard Time
SkipLocaleSelection=YES
UILanguage=en-US
UserLocale=0409:00000409
InputLocale= 0409:00000409
KeyboardLocale= 0409:00000409
EventService=http://WSUS:9800

```


## Applications Installation

```
%SCRIPTROOT%\Joindomain.ps1 #Powershell to automatically joint the DC

cmd.exe /c "%SCRIPTROOT%\vmwaretools.exe /S /v REBOOT

%SCRIPTROOT%\vmwaretools.exe /S /v "/qn REBOOT=R" 

vmware.exe /S /v "/qn REBOOT=R" => works well in Install one application
msiexec /qn /norestart /i googlechromestandaloneenterprise64.msi  works well
MsiExec.exe /i "firefox.msi" /qn works well

```

