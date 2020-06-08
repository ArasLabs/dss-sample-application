# Data Synchronization Services Sample Application

The Data Synchronization Service (DSS) provides Item Actions and Events that you can use to create an environment where data from one Aras Innovator instance can be synchronized with another Aras Innovator instance. These actions and events target the Destination system and are used to add, update, or delete data passed from the Source system to the Destination system.

This sample application is an Aras Community Project. It is not a standard product and should not be deployed to production as-is. The purpose of the sample application is to demonstrate the Data Synchronization Services API capabilities so that custom applications can be built to address specific business requirements and processes.

## History

Release | Notes
--------|--------
[12.0.4.1](https://github.com/ArasLabs/dss-sample-application/releases/tag/12.0.4.1) | Updated to 12.0
[11.0.15.1](https://github.com/ArasLabs/dss-sample-application/releases/tag/11.0.15.1) | First release.

#### Supported Aras Versions
Project | Notes
--------|--------
[12.0.4.1](https://github.com/ArasLabs/dss-sample-application/releases/tag/12.0.4.1) | 12.0 SP4
[11.0.15.1](https://github.com/ArasLabs/dss-sample-application/releases/tag/11.0.15.1) | 11.0 SP15

## Installation

#### Important!
**Always back up your code tree and database before applying an import package or code tree patch!**

### Pre-requisites

1. Aras Innovator installed (version 12.0 SP4)
	* Note: This sample application requires two Innovator instances to install
	* Note: This sample application should be compatible with any version of 12.0 SPX
2. Agent Service installed
3. Conversion Server installed
	* You can refer to the [Sample Guide](https://github.com/ArasLabs/dss-sample-application/blob/master/Documentation/Aras%20Innovator%2011.0%20-%20DSS%20Sample%20Package%20Guide.pdf) for steps on configuring your Conversion Server
4. [Aras Package Import tool](https://www.aras.com/support/downloads)
5. Data Synchronization Services Application package

### Source Install Steps

1. Backup your database and store the BAK file in a safe place
2. Open up the Aras Package Import tool
3. Enter your login credentials and click **Login**
	* _Note: You must login as root for the package import to succeed!_
4. Enter the package name in the TargetRelease field
	* Optional: Enter a description in the Description field
5. Enter the path to your local `..\dss-sample-application\source\eap_imports.mf` file in the Manifest File field
6. Select all of the packages in the Available for Import field
7. Select Type = **Merge** and Mode = **Thorough Mode**
8. Click **import** in the top left corner

### Target Install Steps

1. Open the Aras Package Import tool
2. Enter your login credentials and click **Login**
	* _Note: You must login as root for the package import to succeed!_
3. Enter the package name in the TargetRelease field
	* Optional: Enter a description in the Description field
4. Enter the path to your local `..\dss-sample-application\destination\eap_imports.mf` file in the Manifest File field
5. Select all of the packages in the Available for Import field
6. Select Type = **Merge** and Mode = **Thorough Mode**
7. Click **import** in the top left corner
8. Close the Aras Package Import tool

## Usage

1. Log into the Source System
2. In the TOC, navigate to **Administration/File Handling/Conversion Tasks**. Confirm that there are no tasks with of the LauncherSynchronizationRule
	* If any tasks are of this rule, delete them
3. Navigate to **Administration/Data Synchronization/Innovator Servers**
4. Open the existing item and set the **Server URL Pattern** to the URL of your Target system
5. Navigate to **Administration/Data Synchronization/Synchronization Rules**
6. Open the item and set the following values
	* **Destination Databse** - The name of the database on your Target system
	* **Files Checkout Path** - A folder used to temporarily checkout files during the Synchronization from the Source to the Target System
		* We recommend choosing a folder in the codetree of your Source Aras Innovator instance to ensure that the permissions are correct and a file can be created in the folder.
7. Navigate to **Administration/Methods**
8. Run the **ConversionTaskCreate** method

Your environment should now be configured to allow synchronization from your Source Aras Innovator instance to your Target. For more details on how to run this synchronization, please see Section 4 of the [Sample Guide](https://github.com/ArasLabs/dss-sample-application/blob/master/Documentation/Aras%20Innovator%2011.0%20-%20DSS%20Sample%20Package%20Guide.pdf)

## Contributing

1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -am 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request.

For more information on contributing to this project, another Aras Labs project, or any Aras Community project, shoot us an email at araslabs@aras.com.

## Credits

Sample application created by Aras Development.

## License

Aras Labs projects are published to GitHub under the MIT license. See the [LICENSE file](./LICENSE.md) for license rights and limitations.

