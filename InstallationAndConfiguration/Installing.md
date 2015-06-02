# Installing the NCR Counterpoint API

Installing the NCR Counterpoint API server is simple: run the .msi installer on the machine you wish to be the API Server. By default, the API server will install to `C:\Program Files (x86)\NCR\Counterpoint API`. This path can be changed during the install process if needed.

When the install completes, the server should be up and running on the default port (81). The API installs as a windows service, and can be found under the name "NCR Counterpoint API" in the services console:

![Services console](/InstallationAndConfiguration/NCRCounterpointAPIServicesConsole.png)

To verify the API Server is working correctly, you can try accessing it from a browser on the local machine at https://localhost:81/app/index.htm#/login. This will load the login page to the NCR Counteropint API Management console. If the service does not respond, please ensure it's running by checking the services console (`services.msc`). The only problem we've typically seen with the server not starting or responding is if the port being used by the API server is already used by another process. If this is the case, you can either stop or remove the other process, or change the port that the server is using by editing the `CPAPI.Console.exe.config` file. 

**NOTE** If you change the port that the API Server is using, you will need to unbind your SSL certificate and rebind it to the new port (or install a new certificate and bind it to the new port), otherwise, the SSL certficiate will break and cause issues accessing the server. 

If you have problems accsesing the NCR Counterpoint Admin Console, please see the [troubleshooting wiki page](https://github.com/NCRCounterpointAPI/APIGuide/wiki/Troubleshooting) for help.

Once you've verified the server is running, you can move on to configuring the server.

## Directory structure
Below is a description of the directory structure and key files and locations for the API server. This structure all exists underneath the installation folder, which is assumed below to be the default of `C:\Program Files (x86)\NCR\Counterpoint API`.

Folder | Description | Contents
------ | ----------- | --------
C:\Program Files (x86)\NCR\Counterpoint API | Installation folder | All binaries exist in the installation folder. These files should typically never need to be touched, with the exception of CPAPI.Console.exe.config, which may be edited for things such as configuring the port the server is listening on.
APIKeys | API Key folder | This folder contains API keys for client applications that need access to the system. Developers of 3rd party applications using the API should put their XML key files (not the plain text TXT file) in this folder in order to allow their application to access this server.
App_Data | System data folder | This folder contains the sysadmin.sqlite file, which is a system SQLite database managed internally by the API server. This database holds information like TLD and database connection information, sysadmin login information, and other system level data needed by the API server. The sysadmin.sqlite file will be automatically recreated if deleted, but of course all information stored in the file would be lost, such as links to Counterpoint companies, sysadmin users, etc. All company level information would remain intact once a link to a Counterpoint database is re-established since that data is stored in the Counterpoint database and TLD.
Logfiles | Log folder | This folder holds the log files for the API server (CPAPI.log). There is one logfile for the API server, and by default it is configured as a rolling log file, so each day the log file for the day will be archived as CPAPIyymmdd.log. By default a maximum of 10 days of log files will be kept. The API server uses standard Log4Net logging so the log file can be reconfigured by editing the `<log4net>` node of CPAPI.Console.exe.config per standard log4net specifications.
x64 | 64bit folder | This folder holds binary files that are needed for operation on 64bit machines. There should never be a need to be touched.
x86 | 32bit folder | This folder holds binary files that are needed for operation on 32bit machines. There should never be a need to be touched.

## Permissions
As a web server, all non-administrative functionality should be accessed through the REST API itself, or the web based NCR Counterpoint API Management Console. Windows access to installation folder (and ideally the entire machine hosting the API Server) should be locked down and restricted to administrative access only.

In addition, the NCR Counterpoint API Server needs to be able to access the company specific data it provides via the API, which includes the following:
- Read/Write access to the TLD and all subfolders of the TLD of the companies that are accessible via the API.
- Database administrative access to the Counterpoint databases that are accessible via the API.

## Service Account
By default, the NCR Counterpoint API Service will run under the LocalSystem account, as shown on the "Log On" tab of the property page for the service:

![Service properties](/InstallationAndConfiguration/ServicePropertiesLogOn.png)

This can be changed if needed using the dialog above. Whatever account that is configured for the service to run under is the account that will need to be granted permissions to the afore mentioned TLD folder, as well as the account that will be used to connect to databases that are configured to use integrated security. Please note that the API server can be configured with different database credentials than those in the companies.ini folder, so it is not necessary to grant database admin rights to the database connection in companies.ini.

## Changes to Counterpoint databases
Currently, the only change the API server will make to a Counterpoint database is to add a table called "KeyValueData" to the database. This is why the server needs database administrative access. The table will be added whenever it's found to be missing. The structure of the table is:

Column | Datatype | Description
------ | -------- | -----------
Id | int (Auto-increment) | A unique Id for the object being stored.
Key | varchar(8000) | A unique identifier for the object being stored. For instance, if it's a user role, the name of the user role.
Type | varchar(8000) | The type of data being stored in the "Value" column. This is automatically filled in by the API Server based on the .NET type being stored, and is used to filter out all objects of a given type from the table.
Value | varchar(max) | The object being stored. This is a JSON serialization of the object.

This table is used as a generic storage location for data specific to the API, such as API users (that are tied to Counterpoint SY_USR users), and API roles. The intent is to continue to store company specific data in the Counterpoint company databases, while system/administrative level data is stored in the SQLite database. This also ensures that if a Counterpoint database is ever removed from an API server for some reason, and linked back at a later time (or moved to a different API server), that the proper data continues to live and persist with Counterpoint.

The KeyValueData table stores data objects that are serialized into JSON strings, similar to how a NoSQL database stores data. This allows for very quick reading and writing of data, or accessing of data by Id or Name, but it is not ideal for querying data filtered by specific attributes (such as finding all roles with access to "GET /Customers"). It also allows for easy storage/retrieval of data without having to make data model changes, reducing friction for users and making things easier for developers. However, we currently have little need for that when working with data in this table, and typically the volume of data in the table will be small enough that performance is not a major concern.
