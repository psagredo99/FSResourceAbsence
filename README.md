# FSResourceAbsence

Salesforce package to display resource absences in a calendar (VF + Apex + static resource).

## Included
- Apex: ResourceCalendarController + helpers (CsvBuilder, StringBuilder, HolidayUtil) and tests
- Visualforce page: ResourceCalendar
- Static Resource: ResourceCalendar (JS/CSS/assets)
- Permission Set: ResourceCalendar
- Custom Tab: Resource_Calendar
- Custom Label: CsvColumnsInvalid

## Deploy (manifest)
```
sfdx force:source:deploy -x manifest/package.xml -u <alias>
```

## Post-deploy
1. Assign permission set `ResourceCalendar` to users.
2. Add tab `Resource_Calendar` to the desired app (optional).

## Notes
- The calendar uses FSL objects (ServiceAppointment, ResourceAbsence, ServiceResource). Ensure Field Service is enabled.
- The Custom Label `CsvColumnsInvalid` is included in `force-app/main/default/labels/CustomLabels.labels-meta.xml`.
