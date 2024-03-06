---
external help file: UMN-Google-help.xml
Module Name: UMN-Google
online version:
schema: 2.0.0
---

# Remove-GSheetSheet

## SYNOPSIS
Removes a sheet from a spreadsheet based on sheetID

## SYNTAX

```
Remove-GSheetSheet [-accessToken] <String> [-sheetName] <String> [-spreadSheetID] <String>
 [-ProgressAction <ActionPreference>] [<CommonParameters>]
```

## DESCRIPTION
This function will delete an individual sheet.

## EXAMPLES

### EXAMPLE 1
```
Remove-GSheetSheet -accessToken $accessToken -sheetName 'Name to delete' -spreadSheetID $spreadSheetID
```

## PARAMETERS

### -accessToken
access token used for authentication. 
Get from Get-GOAuthTokenUser or Get-GOAuthTokenService

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -sheetName
Name of sheet to delete

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -spreadSheetID
ID for the target Spreadsheet. 
This is returned when a new sheet is created or use Get-GSheetSpreadSheetID

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: True
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProgressAction
{{ Fill ProgressAction Description }}

```yaml
Type: ActionPreference
Parameter Sets: (All)
Aliases: proga

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

## OUTPUTS

## NOTES

## RELATED LINKS
