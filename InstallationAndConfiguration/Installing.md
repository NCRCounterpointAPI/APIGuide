# Installing the NCR Counterpoint API

Installing the NCR Counterpoint API server is simple: run the .msi installer on the machine you wish to be the API Server. By default, the API server will install to `C:\Program Files (x86)\NCR\Counterpoint API`. This path can be changed during the install process if needed.

When the install completes, the server should be up and running on the default port (81). The API installs as a windows service, and can be found under the name "NCR Counterpoint API" in the services console:

**Need image**

To verify the API Server is working correctly, you can try accessing it from a browser on the local machine at https://localhost:81/app/index.htm#/login. This will load the login page to the NCR Counteropint API Management console. If the service does not respond, please ensure it's running by checking the services console (`services.msc`). The only problem we've typically seen with the server not starting or responding is if the port being used by the API server is already used by another process. If this is the case, you can either stop or remove the other process, or change the port that the server is using by editing the `CPAPI.Console.exe.config` file. 

**NOTE** If you change the port that the API Server is using, you will need to unbind your SSL certificate and rebind it to the new port (or install a new certificate and bind it to the new port), otherwise, the SSL certficiate will break and cause issues accessing the server. 

If you have problems accsesing the NCR Counterpoint Admin Console, please see the troubleshooting page for help.

Once you've verified the server is running, you can move on to configuring the server.

## Directory structure
Below is a description of the directory structure and key files and locations for the API server. This structure all exists underneath the installation folder, which is assumed below to be the default of `C:\Program Files (x86)\NCR\Counterpoint API`.

Folder | Description | Contents
------ | ----------- | --------
C:\Program Files (x86)\NCR\Counterpoint API | Installation folder | All binaries exist in the installation folder. These files should typically never need to be touched, with the exception of CPAPI.Console.exe.config, which may be edited for things such as configuring the port the server is listening on.
APIKeys | API Key folder | This folder contains API keys for client applications that need access to the system. Developers of 3rd party applications using the API should put their XML key files (not the plain text TXT file) in this folder in order to allow their application to access this server.
App_Data | System data folder | This folder contains the sysadmin.sqlite file, which is a system SQLite database managed internally by the API server. This database holds information like TLD and database connection information, sysadmin login information, and other system level data needed by the API server.
Logfiles | Log folder | This folder holds the log files for the API server (CPAPI.log). There is one logfile for the API server, and by default it is configured as a rolling log file, so each day the log file for the day will be archived as CPAPIyymmdd.log. By default a maximum of 10 days of log files will be kept. The API server uses standard Log4Net logging so the log file can be reconfigured by editing the `<log4net>` node of CPAPI.Console.exe.config per standard log4net specifications.
x64 | 64bit folder | This folder holds binary files that are needed for operation on 64bit machines. There should never be a need to be touched.
x86 | 32bit folder | This folder holds binary files that are needed for operation on 32bit machines. There should never be a need to be touched.
