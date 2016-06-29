# A Primer About Software Engineering
# Appendix: Cmd

Don't install SQL Server with the UI.

It's important to be able to replicate installing the SQL Server consistently on every developer machine. Fortunately you can install SQL Server from the command line with a *ConfigurationFile.ini*. The Installation Wizard can generate that for your.


## Generating a ConfigurationFile.ini

* Download [SQL Server 2014 Express](https://www.microsoft.com/en-US/download/details.aspx?id=42299).
* Unpack it into a folder of your choice.
* Open a shell
* `cd` into that directory, you should find a nice `SETUP.EXE`.
* Generate a ConfigurationFile.ini with the Wizard `SETUP.exe /UIMODE=Normal /ACTION=INSTALL` 
* Configure everything you want in the Wizard but __STOP__ before clicking install.
* The Wizard should show you the location of your ConfigurationFile.ini
* Copy the ConfigurationFile.ini to the directory of your SETUP.EXE and cancel the wizard.

You can look up more information about the [Configuration File](https://msdn.microsoft.com/en-us/library/dd239405(v=sql.120).aspx) and the possible [parameters](https://msdn.microsoft.com/en-us/library/ms144259(v=sql.120).aspx) online.


## Installing SQL Server with a ConfigurationFile.ini

* `cd` into unpacked SQL Server directory
* Provide the SA Password via command line
* `SETUP.EXE /SAPWD=”passwordhere” /ConfigurationFile="ConfigurationFile.ini" /IAcceptSQLServerLicenseTerms`

## Installing SQL Server via Command Line

* `cd` into unpacked SQL Server directory
* Provide the Instance name from your ConfigurationFile.ini via command line
* `SETUP.EXE /FEATURES=SQL,AS,RS,IS,Tools /INSTANCENAME=INSTANCENAMEHERE`
