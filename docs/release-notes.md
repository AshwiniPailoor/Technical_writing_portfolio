# CareSync Release Notes

---

## Version 4.2.0 — January 2025

### What's New

**Patient Timeline View (Beta)**  
You can now view a patient's complete care history as a chronological timeline. 
Access it from the patient profile by clicking **Timeline** in the top navigation.

**Bulk Appointment Scheduling**  
Schedule recurring appointments for up to 50 patients simultaneously. 
Navigate to **Scheduling → Bulk Actions** to get started.

**EHR Integration: Epic MyChart**  
CareSync now integrates directly with Epic MyChart, allowing patients to 
self-schedule appointments through the MyChart portal. 
See the [Epic Integration Setup Guide](#) to configure this for your facility.

---

### Improvements

- **Performance:** Dashboard load time reduced by 40% for facilities with more than 10,000 patient records.
- **Accessibility:** All form fields now include ARIA labels, improving compatibility with screen readers.
- **Search:** Patient search now returns results as you type, rather than requiring you to press Enter.

---

### Bug Fixes

| Issue | Description |
|-------|-------------|
| CS-1847 | Fixed a bug where appointment reminders were sent twice for recurring bookings |
| CS-1901 | Resolved a display issue where patient names with special characters appeared garbled in PDF exports |
| CS-1923 | Fixed an error that prevented logging out while a file upload was in progress |

---

### Deprecation Notice

**Legacy API v1 endpoints** will be retired on **June 30, 2025**. 
Migrate to the v2 API before this date to avoid service interruption. 
See the [v1 to v2 Migration Guide](#) for step-by-step instructions.

---

## Version 4.1.2 — December 2024

### Bug Fixes

- Fixed an issue where the insurance verification module timed out for 
  facilities in the UTC-8 timezone.
- Resolved a conflict between the mobile app and two-factor authentication 
  when using hardware security keys.

---

*This is a writing sample created for portfolio purposes. CareSync is a fictional product.*
