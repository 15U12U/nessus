# Nessus Credential Based Scanning
## Using a non-default Windows Administrator Account
### Prerequisites

- The WMI service must be enabled on the target.
- The Remote Registry service must be enabled on the target.
- File & Printer Sharing must be enabled in the target’s network configuration.
- Ports 139 and 445 must be open between the Nessus scanner and the target.
- An SMB account must be used that has local administrator rights on the target.
- Verify the following,
  ```
  Administrative Tools
    > Local Security Policy
      > Security Settings
        > Local Policies
          > Security Options
            > Network access: Sharing and security model for local accounts
              # Classic - local users authenticate as themselves
  ```
- Windows User Account Control (UAC) must be disabled
  - Method 1: Open the **Control Panel**, select **User Accounts** and then set **Turn User Account Control** to **Off**
  - Method 2: Change the registry DWORD named **EnableLUA** to "**0**" at the following location:
    ```
    HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\EnableLUA
    ```
  - Method 3: Add a new registry DWORD named **LocalAccountTokenFilterPolicy** and set the value to "**1**" at the following location:
    ```
    HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\LocalAccountTokenFilterPolicy
    ```



