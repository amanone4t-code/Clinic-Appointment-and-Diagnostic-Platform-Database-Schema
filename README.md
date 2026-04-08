# Clinic-Appointment-and-Diagnostic-Platform-Database-Schema

A relational database for managing doctors, patients, appointments, consultations, prescriptions, diagnostic tests, payments, and reports.

## Tables

| Table | Description |
|---|---|
| `specialty` | Medical specializations lookup |
| `doctors` | Doctor profiles and credentials |
| `patients` | Patient demographics and contact info |
| `appointment` | Scheduled doctor-patient visits |
| `consultation` | Completed consultation records |
| `prescription` | Medications prescribed per consultation |
| `diagnostic_test` | Catalog of available lab/diagnostic tests |
| `prescribed_test` | Tests ordered via a prescription |
| `report` | Results from prescribed tests |
| `payment` | Transactions for consultations and prescriptions |

## Relationships

```
specialty        ──< doctors
doctors/patients ──< appointment
appointment      ──1 consultation
consultation     ──< prescription ──< prescribed_test ──1 report
consultation     ──< payment
prescription     ──< payment
diagnostic_test  ──< prescribed_test
```

## Notes

- All clinical activity flows from `appointment` → `consultation` → `prescription` / `payment`
- Payments link to either a consultation or prescription for flexible billing
- Most tables carry ENUM status fields for lifecycle tracking
