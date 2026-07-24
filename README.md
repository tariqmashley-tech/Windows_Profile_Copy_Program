# Windows Profile Copy Program

## Section 1: Project Overview

The **Windows Profile Copy Program** was developed to streamline the migration of user profiles from traditional on-premises **Active Directory (AD)** environments to **Microsoft Entra ID**. As the organization transitioned to a hybrid identity infrastructure, the application automated the migration of user profile data, configuration settings, and personal files from legacy AD profiles to newly created Entra profiles. By minimizing manual intervention, the tool significantly reduced user downtime, improved the migration experience, and allowed employees to resume work with little to no reconfiguration after signing into their new Entra accounts.

---

# Section 2: Business Problem

### Challenge

The organization currently operates in a hybrid environment where some services remain on local infrastructure while others have been migrated to the cloud. Although Microsoft 365 services had already been adopted, user authentication and Windows profiles were still managed through an on-premises Active Directory server.

To repurpose the local Active Directory server and continue the organization's cloud migration strategy, users needed to begin signing into their computers using their Microsoft Entra ID (Microsoft 365) accounts instead of their local AD accounts.

Unfortunately, Windows treats an Entra profile as an entirely new user profile. Without migration, each employee would have been required to manually rebuild their Windows environment by:

* Reconfiguring application settings
* Restoring user preferences
* Recreating desktop layouts
* Reconnecting application data
* Potentially reinstalling profile-based software
* Manually copying personal documents and files

### Impact

This process would have affected every employee in the organization, resulting in:

* Significant downtime
* Lost productivity
* Increased Help Desk workload
* Inconsistent user experiences
* Longer migration timelines

Because dozens of users required migration, manually rebuilding each profile was not a practical or efficient solution.

---

# Section 3: Technical Solution

To address this challenge, I designed and developed a Windows desktop application in **C#** that automates the migration of user profile data between local Active Directory profiles and Microsoft Entra profiles.

The application guides an administrator through the migration process by requesting:

1. The source Active Directory profile path.
2. The destination Microsoft Entra profile path.

After validating the supplied directories, the program leverages **Microsoft RoboCopy**, a highly reliable Windows file replication utility, to copy profile-specific data between the two locations.

The migration includes:

* Desktop
* Documents
* Downloads
* Pictures
* Music
* Videos
* Favorites
* AppData\Roaming (application settings)
* Other profile-specific folders and configuration files

During execution, the application displays a real-time status window showing:

* Current file being copied
* Progress of the migration
* Files skipped
* Copy statistics
* Any errors encountered

If a file cannot be copied, the application reports the reason, such as:

* Insufficient permissions
* Locked files
* Missing directories
* Invalid paths

After completion, the application presents a summary report detailing:

* Successful copies
* Failed items
* Total files processed
* Overall migration status

Finally, the program instructs the administrator to have the user sign out and back into their Microsoft Entra profile to verify that the migrated profile has been successfully applied.

This automated approach dramatically reduces the time required for profile migration while preserving user settings and minimizing workflow interruptions.

---

# Section 4: Technologies Used

### Programming Languages

* C#

### Framework

* .NET

### Development Environment

* JetBrains Rider

### Operating Systems

* Windows 10
* Windows 11

### Identity Platforms

* Active Directory
* Microsoft Entra ID

### Supporting Technologies

* RoboCopy
* Windows User Profiles
* Windows File System
* NTFS Permissions

---

# Section 5: Screenshots

* Application startup screen
<img width="670" height="382" alt="image" src="https://github.com/user-attachments/assets/3e156426-cb40-4a35-8476-74659e04d462" />

* Source and destination profile selection
<img width="668" height="383" alt="image" src="https://github.com/user-attachments/assets/a4b90555-79c5-43a8-8c9b-956fcc6aafe4" />

* Validation screen
* Migration progress window
* RoboCopy execution log
* Error reporting example
* Completion summary
* Successful migration confirmation

These screenshots provide visual evidence of the application's functionality and improve documentation quality.

---

# Section 6: Lessons Learned

Developing this project provided valuable experience with Windows profile management, identity migration, and automation.

### Key Lessons Learned

* Understanding the differences between Active Directory and Microsoft Entra user profiles
* Managing Windows profile folder structures and application dependencies
* Automating administrative tasks using C#
* Integrating external command-line utilities (RoboCopy) into desktop applications
* Implementing robust error handling and status reporting
* Working with Windows permissions and file ownership
* Validating user input before executing system-level operations
* Testing migration workflows in production-like environments
* Designing applications that improve the end-user experience while reducing IT support effort

The project also reinforced the importance of automation in reducing repetitive administrative work and improving organizational efficiency during large-scale infrastructure transitions.

---

# Section 7: Future Improvements

Several enhancements have been identified that could further improve the application's functionality and scalability.

### Planned Improvements

* Develop a graphical wizard for an even more intuitive user experience
* Automatically detect available local and Entra profiles
* Integrate directly with Microsoft Graph and Microsoft Entra APIs
* Add detailed migration logging with exportable reports (CSV/PDF)
* Generate automated migration success reports
* Verify profile integrity after migration
* Add rollback capabilities if a migration encounters critical failures
* Support batch migrations for multiple users
* Add PowerShell integration for automated enterprise deployments
* Integrate with Microsoft Intune to support cloud-managed device provisioning

These enhancements would further reduce administrative effort, improve migration accuracy, and better support large-scale enterprise identity modernization initiatives.
