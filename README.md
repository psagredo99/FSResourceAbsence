# FSResourceAbsence – Custom Resource Calendar

Salesforce package to display **Service Appointments** and **Resource Absences** in a unified calendar view.  
The component is designed for **dispatchers, supervisors, and operations teams**, providing visibility of workload, availability, and absences in a single interface.

The solution is implemented using **Visualforce, Apex, and Static Resources**, and is compatible with **Salesforce Field Service (FSL)**.

---
<img width="1918" height="778" alt="image" src="https://github.com/user-attachments/assets/286d7a37-f76e-44ea-9738-aea32694d5b9" />


## UI Reference – Calendar Component

### 1. Calendar Export (CSV)
Provides the ability to **export the current calendar view to a CSV file**.  
The exported file includes all visible entries in the calendar (service appointments and resource absences), respecting the **active filters, date range, and view mode** applied at the time of export.

This allows:
- Offline analysis and reporting  
- Sharing schedules with external systems or stakeholders  
- Data reconciliation and auditing  

---

<img width="1634" height="499" alt="image" src="https://github.com/user-attachments/assets/cef9a2c8-e29c-4a9f-b0aa-437246ae604c" />


### 2. Work Type Selector
Dropdown used to filter calendar entries by **Work Type** (e.g. Repair, Preventive, Remote Assistance).  
This affects which service appointments are displayed and how the operational load is visualized.

---

### 3. Global Search
Text-based search applied to the calendar content.  
Allows filtering by identifiers such as:
- Service Appointment number  
- Work Order reference  
- Customer or site keywords  

---

<img width="1636" height="680" alt="image" src="https://github.com/user-attachments/assets/d4ae3e71-f71b-4572-ae59-2b1ceb1ef985" />


### 4. Calendar View Mode
Switch between different calendar visualizations:
- **Month**: High-level planning and load overview  
- **Week**: Medium-term scheduling and balancing  
- **Day**: Detailed operational view  
- **List**: Tabular representation of appointments and absences  

---

<img width="1891" height="582" alt="image" src="https://github.com/user-attachments/assets/2485e57f-c262-4403-8b55-99c35b27a876" />

### 5. Zone Filter
Filter resources and events by **Zone / Territory**.  
Useful for dispatchers managing multiple geographic or operational areas.

---

### 6. Resource Absence Toggle
Option to display **only resource absences** (vacations, medical leave, unavailable periods).  
Helps supervisors focus exclusively on capacity and availability constraints.

---

### 7. Resource Panel
Scrollable list of **Service Resources** included in the current view:
- Allows showing **all resources** or **only the current user**
- Acts as a contextual filter for the calendar
- Supports mixed visualization of appointments and absences per resource

---

## Package Contents

### Included
- **Apex**
  - `ResourceCalendarController`
  - Helper classes: `CsvBuilder`, `StringBuilder`, `HolidayUtil`
  - Unit tests
- **Visualforce Page**
  - `ResourceCalendar`
- **Static Resource**
  - `ResourceCalendar` (JavaScript, CSS, assets)
- **Permission Set**
  - `ResourceCalendar`
- **Custom Tab**
  - `Resource_Calendar`
- **Custom Label**
  - `CsvColumnsInvalid`

---

## Deployment

### Deploy (manifest)
```bash
sfdx force:source:deploy -x manifest/package.xml -u <alias>
```

---

## Post-Deployment Steps

1. Assign the permission set **`ResourceCalendar`** to the target users.
2. Add the **`Resource_Calendar`** tab to the desired Lightning App (optional).

---

## Scope & Assumptions

- The calendar works with standard **Salesforce Field Service objects**:
  - `ServiceAppointment`
  - `ResourceAbsence`
  - `ServiceResource`
- **Field Service must be enabled** in the target org.
- Data quality (zones, work types, absences, assignments) is assumed to be managed upstream by standard FSL configuration or integrations.
- The CSV export reflects **exactly what is visible in the UI** at export time.

---

## Notes

- The Custom Label **`CsvColumnsInvalid`** is included in  
  `force-app/main/default/labels/CustomLabels.labels-meta.xml`.
- This component focuses on **visualization and export**; it does not replace the standard Dispatcher Console.
- Designed to complement FSL when a **calendar-centric, absence-aware view** is required.

---

## Credits

Developed and maintained by **Pablo Sagredo**.

---

## License
Internal / Project-specific usage. Adapt as required for open-source distribution.
