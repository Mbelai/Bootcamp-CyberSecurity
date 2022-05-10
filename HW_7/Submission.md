

# Musie Belai HW7 Submission

## Task 1 ##
Deliverable for Task 1: Take a screenshot of all the GPOs created for this homework assignment. To find these, launch the Group Policy Management tool, select Group Policy Objects, and take a screenshot of the GPOs you've created.

 ![GPO.png](./image/GPO.png)   

## Task 2 ##
Deliverable for Task 2: Submit a screenshot of the different Account Lockout policies in Group Policy Management Editor. It should show the three values you set under the Policy and Policy Setting columns.

![AccountLockout.png](./image/AccountLockout.png)
![AccountLockout2.png](./image/AccountLockout2.png)

## Task 3 ##
Deliverable for Task 3: Submit a screenshot of the different Windows PowerShell policies within the Group Policy Management Editor. Four of these should be enabled.

![WindowsPowershell](./image/WindowsPowershell.png)

## Task 4 ##
Deliverable for Task 4: Submit a copy of your enum_acls.ps1 script.

        $directory = Get-ChildItem
        foreach ($item in $directory) {
        Get-Acl .\
        }
        
## Task 5 ##
Deliverable for Bonus Task 5: Submit a screenshot of the contents of one of your transcribed PowerShell logs or a copy of one of the logs.

![Log.png](./image/Log.png)
![PowerShell_transcript.DESKTOP-SITPOTH.hHTr8tfo.20220509205437.txt](image\PowerShell_transcript.DESKTOP-SITPOTH.hHTr8tfo.20220509205437.txt)