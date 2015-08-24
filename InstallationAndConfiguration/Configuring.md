# Configuring the NCR Counterpoint API Server

Once the server is installed and running, it must be configured per the requirements needed in it's environment. There are a few items that should be setup to prepare the API server for use:
* Creating System Administrators
* Adding Companies
* Designating Company Administrators
* Creating and Assigning Roles

## Creating System Administrators
System Administrators have the ability to add and remove company access via the API server, as well as designating company administrators within each company. By default, there is a single system administrator login created during installation with the name/password of "admin"/"password". It is recommended that the password be changed on this user immediately upon login. It is also recommended that logins should not be shared. Each individual with authority should have their own system administrator login created, that is to be used only by them. To create a system administrator login:
* Login to the API administrator console at `https://<apiservername>:<port>/app/index.htm#/login` using an existing system administrator login ("admin") if this is a brand new system
* Select "Configuration" > "Add Admin User"
* Enter a User ID for and password for the new Admin user
* Click "OK" to save the user

## Adding Companies
In order for the API server to do anything useful, it must be told how to connect to existing Counterpoint companies that it will serve. This is done by "adding" a company to the API server. If the API server was installed on a machine that has previously had Counterpoint installed, it will attempt to do this automatically per these rules:
* Check the registry to see if a path to a Counterpoint install exists at HKLM\Software\[Wow6432Node]\Synchronics\CounterPoint\8.0\InstallPath
* If a valid install path exists, look in the "TopLevel" subdirectory off of that path for a companies.ini file
* If a companies.ini file is found, each company in the file will be automatically added to the API server

To see what companies, if any, the API server is aware of:
* Login to the API administrator console at `https://<apiservername>:<port>/app/index.htm#/login` using a system administrator login
* Select "Configuration" > "Companies"
A list of companies the API server is aware of will be displayed. Note that companies can be disabled without removing them from the server, which will prevent access to the company.

If you need to add companies to the API server:
* Login to the API administrator console at `https://<apiservername>:<port>/app/index.htm#/login` using a system administrator login
* Select "Configuration" > "Companies"

There are two ways to add companies: Manually and automatically via an existing companies.ini.
To add a company manually:
* Click the "Add" button on the Companies screen
* Enter all the required information to allow the server to connect to the company
  * Name: This is an alias for the company. It is highly recommended that this match the company alias in the companies.ini file
  * TLD: This is a path to the TLD from the server. The server must have read access to the TLD. This can be a UNC path
  * Server: The name or IP address of the SQL server hosting the Counterpoint database
  * Database: The database name in SQL Server
  * Security: Select either "Integrated Security" or "SQL Security" depending on your needs. If "SQL Security is chosen, you'll also need to enter a SQL username & password.
NOTE: The SQL credentials used by the server must allow full read/write access to all Counterpoint tables, as well as permissions to create tables (The API server does create a table in the company DB to store company specific API configuration data)
* Click "OK" to save the company

To add a company automatically via companies.ini:
* Click the "Add from cmopanies.ini" button on the Companies screen
* Enter a path to the TLD containing the companies.ini (from the server's perspective). This can be a UNC path.
* Click "OK"
* If a valid companies.ini is located, a list of company alias from the file will be displayed. Select the checkbox next to each company you wish to add.
* Click "OK"

## Designating Company Administrators
By default, NCR Counterpoint users don't have access to their data via the API server, even after the company is added. The system administrator must identify existing NCR Counterpoint users who should have authority to administer the company. Company administrators have the ability to create and edit roles, as well as assign and unassign roles from other Counterpoint users in their company. Only system administrators can add & remove company administrators. To add a company administrator:
* Login to the API administrator console at `https://<apiservername>:<port>/app/index.htm#/login` using a system administrator login
* Select "Configuration" > "Companies"
* Click on the desired company name to expand the details of the company connection
* In the "Company Admins" section, select "Edit Admins"
* A list of Counterpoint users in the given company will be displayed. Select the checkbox next to each user that should be given company admin privledges.
* Click "OK" to save your changes

## Creating and Assigning Roles
Roles determine what API calls a given user can make. Roles are defined, then assigned to company level users. To create a role:
* Login to the API administrator console at `https://<apiservername>:<port>/app/index.htm#/login` using a company administrator login (NOTE: company logins should always enter `<CompanyAlias>.<Counterpoint User name>` for their API User ID, for example "TESTGOLF.MGR")
* Select "Roles" > "Edit Roles"
* Enter the name for the new role and click "Add New Role"
* The new role will be added immediately. Click on the role name to exand it, then click on "Endpoints" to expand the list of API endpoints
* Select the checkbox for each Endpoint/Verb combination (API Call) that the role should allow. For convenience, checking on a http verb in the header column ("GET", "POST", etc.) will select all endpoints for that verb. Similarly, clicking on the endpoint name ("/Customer/{CustNo}") will select all verbs for that endpoint. If there is no checkbox visible for a given endpoint/verb combination, then that call does not exist
* Click "Save Endpoints" to save the new role

To assign the role to Counterpoint users:
* Select "Roles" > "Edit User Roles"
* Click on a user name to see a list of roles already assigned to the user
* Click on "Assign User Roles"
* Select the checkbox for each role to assign to the user
* Click "OK"

Similarly, you can select multiple users to assign to a single role at once:
* Select "Roles" > "Edit Roles"
* Click on the role name you wish to add users to in order to expand it
* Click on the "Users" header to expand it. You'll see a list of users already assigned to the role, if any
* Click "Edit Users"
* Select the checkbox next to each user the role should be assigned to
* Click "OK"

