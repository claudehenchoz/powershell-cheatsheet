# powershell-cheatsheet
A cheat-sheet for PowerShell snippets

## Select Expression - Modify the value of one property in a pipeline

When working in a pipeline, it is sometimes necessary to either rename a property or to
change its value.

We'll be using the select statement and select an existing property, but add a new one that
is based on a calculation of an existing one.

### Syntax

    select Property1, @{Name="NewPropertyName";Expression={ $_.Property2 * 2 } } 

### Usage

This example enumerates all attached disks, then selects the drive letter and a calculated
FreeGigabytes-property (the expression turns bytes into gigabyes)

    PS C:\> Get-WmiObject Win32_LogicalDisk | select DeviceID, @{Name="FreeGigabytes";Expression={ [int]($_.FreeSpace / 1GB) } }

    DeviceID FreeGigabytes
    -------- -------------
    C:                 190
    D:                 134
    E:                5469

## The PSCustomObject-type - Create a custom object

### Syntax

    [PSCustomObject]@{
        Property1 = "Value 1"
        Property2 = 2
    }

