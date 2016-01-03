# powershell-cheatsheet
A cheat-sheet for PowerShell snippets

## Select Expression - Modify the value of one property in a pipeline

### Syntax

    select Property1, @{Name="NewPropertyName";Expression={ $_.Property2 * 2 } } 

### Usage

    PS C:\> Get-WmiObject Win32_LogicalDisk | select DeviceID, @{Name="FreeGigabytes";Expression={ [int]($_.FreeSpace / 1GB) } }

    DeviceID FreeGigabytes
    -------- -------------
    C:                 190
    D:                 134
    E:                5469
