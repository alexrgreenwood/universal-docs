---
description: Icon component for Universal Dashboard
---

# Icon

[FontAwesome ](https://fontawesome.com/?from=io)icons to include in your dashboard. Icon names are slightly different than those shown on the FontAwesome website. For example, if you want to use the `network-wired` icon, you would use the following string.&#x20;

```powershell
New-UDIcon -Icon 'NetworkWired'
```

## Icon

Create icons by specifying their names. You can use the icon reference below to find icons.

```powershell
New-UDIcon -Icon 'AddressBook'
```

![](<../../../../.gitbook/assets/image (104).png>)

## Size

Set the size of the icon. Valid values are: `xs`, `sm`, `lg`, `2x`, `3x`, `4x`, `5x`, `6x`, `7x`, `8x`, `9x`, `10x`

```powershell
    New-UDIcon -Icon 'AddressBook' -Size 'sm'
    New-UDIcon -Icon 'AddressBook' -Size 'lg'
    New-UDIcon -Icon 'AddressBook' -Size '5x'
    New-UDIcon -Icon 'AddressBook' -Size '10x'
```

![](<../../../../.gitbook/assets/image (105).png>)

## Rotation

Rotate icons. The value represents the degrees of rotation.

```powershell
New-UDIcon -Icon 'AddressBook' -Size '5x' -Rotation 90
```

![](<../../../../.gitbook/assets/image (106).png>)

## Border

Add a border to your icon.

```powershell
New-UDIcon -Icon 'AddressBook' -Size '5x' -Border
```

![](<../../../../.gitbook/assets/image (107).png>)

## Style

Apply CSS styles to your icon.

```powershell
New-UDIcon -Icon 'AddressBook' -Size '5x' -Style @{
    backgroundColor = "red"
}
```

![](<../../../../.gitbook/assets/image (108).png>)

## Visually Search for Icons

```powershell
New-UDTextbox -Id 'txtIconSearch' -Label 'Search' 
New-UDButton -Text 'Search' -OnClick {
    Sync-UDElement -Id 'icons'
}

New-UDElement -tag 'p' -Content {}

New-UDDynamic -Id 'icons' -Content {
        $Icons = [Enum]::GetNames([UniversalDashboard.Models.FontAwesomeIcons])
        $IconSearch = (Get-UDElement -Id 'txtIconSearch').value
        if ($null -ne $IconSearch -and $IconSearch -ne '')
        {
        $Icons = $Icons.where({ $_ -match $IconSearch})
    }

    foreach($icon in $icons) {
        New-UDChip -Label $icon -Icon (New-UDIcon -Icon $icon)
    }
}
```

## Complete Icon List

[Click here to view the complete icon list. ](https://gist.github.com/adamdriscoll/8a5d12b0ac5641bc1083bebf921f56fe)

## API

****[**New-UDIcon**](https://github.com/ironmansoftware/universal-docs/blob/master/cmdlets/New-UDIcon.txt)****
