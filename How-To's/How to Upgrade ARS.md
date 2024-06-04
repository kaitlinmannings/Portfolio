# How to Upgrade Active Roles Server (ARS) from Version 7.0x to 8.1.1

## Product Name: Active Roles Server (ARS)
**Owner:** [Team Name]
**Version:** 1.0
**Phase:** N/A
**Date:** 5/22/2023

## Table of Contents
  1. [Change Record](#change-record)
  2. [Overview](#overview)
  3. [Features](#features)
  4. [Element 1: Creating a Support Account for ARS](#element-1-creating-a-support-account-for-ars)
  5. [Element 2: Preliminary Steps to Upgrade](#element-2-preliminary-steps-to-upgrade)
  6. [Element 3: Upgrade Process](#element-3-upgrade-process)
  7. [Conclusion](#conclusion)
  8. [References](#references)

## Change Record
  | Date       | Author           | Version | Change Description |
  |------------|------------------|---------|---------------------|
  | 5/22/2023  | Kaitlin Mannings | 1.0     | Document Creation   |

## Overview
  This document is a how-to guide on upgrading ARS from version 7.0x to 8.1.1.
  Element 1 explains how to set up a new account with One Identity in order to
  download ARS. If you already have an account, please skip to Element 2.

## Features
### Element 1: Creating a Support Account for ARS
  1. **Visit** [One Identity Support](https://support.oneidentity.com)
  2. **In the top right corner**, click on the icon and choose “Create Support
    Account”
  3. **Fill in all the required fields.**
  4. **Click [Sign Up]** after completing all fields successfully.
  5. **Enter the verification code** sent to your email and click [Verify].
  6. **Register your account** by selecting “Register using your license number”
    and provide your account number. Choose “Active Roles” as the product.
  7. **Complete your profile** by ensuring all required fields are filled out
    and click [Complete Profile].
  8. **Download Latest Software** by clicking on the option.
  9. **Navigate to Access Management** and click [Active Roles].
  10. **Choose the version** 8.1.1 and click the download icon to begin the download.
  11. **Agree to terms** by clicking the checkbox next to “I agree to the above”
    and click [Continue]. Optionally, check “By clicking the check box you can skip this message going forward and go directly to Download Now” and “Active Roles 8.1.1 Release Notes.”

### Element 2: Preliminary Steps to Upgrade
  **Note:** Be sure to review all scripts prior to executing.

  1. **Copy to Hosts**
   - After downloading the software, copy it to all ARS hosts in the file
    [placeholder for file directory].

2. **Creation of Folder**
   - Create the folder that will contain all files, scripts, etc., used during
     the upgrade process.
   - Save locally and copy to each server into [placeholder for file directory].
   - Copy SPML configuration files from the current ARS program files folder
     [placeholder for file directory & file name].
   - Copy to [placeholder for file directory] on each ARS SPML host.
   - Expand the files by going to the file directory, right-clicking, and
     selecting [Mount].
   - Select all files by pressing [Ctrl]+A, right-click, and select [Copy].
   - Navigate to [placeholder for file directory] and paste the files.

3. **Backup Encryption Key**
   - Take a backup of all encryption keys (Note: This step can be done any time
     prior to upgrade and needs to be done only on the primary host where most
     scripts are executed from).

4. **Move Web Service to Debug OU**
   - Move all web service hosts to the debug OU.
   - Open Command Line and run the script located in [placeholder for file directory].

5. **Place all versions in Safe Mode**
   - Place all current version services in Safe Mode, which is a troubleshooting
     option that starts the Administration Service in a limited state.
   - Check the status by running the command `Get-ARService` to see if it is
     already in safe mode.
   - If not, run the command `Set-ARService -SafeModeEnabled $True`.
   - Confirm safe mode status by running the command `Get-ARService`, then
     `Restart-ARService`.
   - The console will show the status in Safe Mode with a warning.

6. **Disable Port Security for SQL Server**
   - Note: For future upgrades past version 8.x, port security for SQL Server
     must be disabled prior to breaking replication.
   - Run the PS SQL security off script on all SQL database instances/servers.
   - Restart all SQL services.
   - Reconnect one service host per SQL database to [placeholder for port].

7. **Break Replication**
   - Break replication by deleting all subscribers from the publisher database,
     then demote the publisher.
   - Open Console.
   - Navigate to Configuration > Server Configuration > Configuration Databases.
   - Delete the Subscriber and confirm by clicking [Yes].

8. **Stop all Services**
   - Open PowerShell ISE.
   - Run the script from [placeholder for file directory], script name: “Example.ps1”.
   - Validate that the services are stopped by running the validation script.

9. **Backup the Database**
   - Connect to the [placeholder] server.
   - Open Microsoft SQL Server Management as Administrator.
   - Expand Databases, right-click on [CurrentVersion Database], and click Back Up.
   - Save the backup as “[CurrentVersion].bak”.

10. **Backup the Configuration File**
    - Switch back to the ARS box.
    - Open Active Roles Sync Service.
    - Export the configuration and save as [placeholder for file name].

### Element 3: Upgrade Process
1. **Clean Install**
   - Uninstall the current version 7.x from the servers.
   - In Control Panel > Programs and Features, right-click on One Identity
     Active Roles and select [Uninstall/Change].
   - Remove the program and restart the system.

2. **Delete One Identity Registry Tree**
   - Confirm ARS Software is fully uninstalled.
   - Open Command Prompt and type `regedit`.
   - Navigate to Software > One Identity > Active Roles, right-click, and delete
     the registry tree.

3. **Initial Install of ARS Software**
   - Install ARS 8.x software using Command Line silent install.
   - Launch PowerShell as administrator and run the installation command:
     ```sh
     D:\install.dr\ARS811\ActiveRoles.exe /quiet /install /IAcceptActiveRolesLicenseTerms
     ```

## Conclusion
   By following these steps, you can successfully upgrade ARS from version 7.0x to 8.1.1. Ensure all procedures are followed accurately to maintain system integrity and functionality.

## References
  - [Quest Active Directory Documentation](https://support.quest.com/)
  - [Microsoft Active Directory Documentation](https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/getting-started/virtual-dc/active-directory-domain-services-overview)
