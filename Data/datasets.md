# Guide to Key English Healthcare Datasets: ECDS, HES APC & HES OP

---

# Emergency Care Data Set (ECDS)

## Overview
The **Emergency Care Data Set (ECDS)** is the national reporting standard for **Urgent and Emergency Care** services in England. It captures structured information on:

- Patient demographics  
- Arrival details and mode  
- Clinical assessments  
- Diagnoses & Comorbidities (SNOMED CT)  
- Investigations, treatments, referrals  
- Discharge status and destination  

It is designed to reflect a complete clinical picture of an ED attendance, including both **pre-existing** and **newly identified** conditions.


## Comorbidities vs Diagnoses

### **Comorbidity Columns**
- Represent conditions known *prior to* or *at* ED arrival.
- Typically sourced from the patient’s primary care record.
- Encoded in **SNOMED CT**.
- Up to **10 comorbidities** can be recorded.

### **Diagnosis Columns**
- Capture all conditions diagnosed during the ED spell.
- Ordered by relevance:  
  - `diagnosis_code_1` = most relevant/serious  
  - up to `diagnosis_code_12`  
- Example ordering: fracture → arrhythmia → chronic heart failure.

This distinction enables analysts to identify chronic disease burden vs acute clinical findings.


## Key Columns in ECDS

### **Identifiers & Demographics**
| Column | Meaning |
|--------|---------|
| `token_person_id` | Pseudonymised patient identifier for linkage. |
| `age_at_arrival` | Age in years at ED attendance. |
| `lsoa_2011` | Geographic code for deprivation and segmentation. |

### **Attendance Context**
| Column | Meaning |
|--------|---------|
| `arrival_date` | Date/time of ED arrival. |
| `provider_code` | NHS trust providing care. |
| `department_type` | ED type (Type 1, 2, 3, UTC). |
| `treatment_function_code` | Responsible clinical specialty. |

### **Arrival & Referral**
| Column | Meaning |
|--------|---------|
| `arrival_mode` | Walk-in, ambulance, referral, etc. |
| `attendance_source` | GP, self, NHS 111, community. |
| `referred_to_service_{1–4}` | Up to four onward services (e.g., fracture clinic). |

### **Clinical Information**
| Column | Meaning |
|--------|---------|
| `health_resource_group` | HRG code for costing. |
| `diagnosis_code_{1–12}` | SNOMED CT diagnoses made in ED. |
| `comorbidities_{1–10}` | Pre-existing conditions. |

### **Discharge**
| Column | Meaning |
|--------|---------|
| `discharge_destination` | Home, admission, transfer, etc. |
| `discharge_status` | Clinical status at discharge. |
| `accommodation_status` | Housing status (e.g., no fixed abode). |

--- 

# Hospital Episode Statistics – Admitted Patient Care (HES APC)

## Overview
HES APC captures all inpatient activity in NHS hospitals in England. Each row represents a **Finished Consultant Episode (FCE)** — a period of care under a single consultant.

Key concepts:

### **Finished Consultant Episode (FCE)**
- Continuous care under one consultant.
- Recorded in the financial year it **ends**.
- Analysts must remove **unfinished episodes** to avoid double counting.

### **Spell**
- A full, uninterrupted inpatient stay at one hospital.
- May contain multiple FCEs if transferred between specialties.
- Transfer to a different hospital = new spell.

## Key Columns in HES APC

### **Identifiers & Demographics**
| Column | Meaning |
|--------|---------|
| `token_person_id` | Pseudonymised patient identifier. |
| `susspellid` | Spell identifier for grouping FCEs. |
| `sushrg` | HRG code for costing. |
| `lsoa11` | Patient’s small-area geographic location. |

### **Clinical Information**
| Column | Meaning |
|--------|---------|
| `diag_{1–20}` | ICD-10 diagnosis list for the episode (primary + secondary). |
| `tretspef` | Treatment specialty. |

### **Episode Timing**
| Column | Meaning |
|--------|---------|
| `epistart` | FCE start date. |
| `epiend` | FCE end date. |
| `admidate` | Admission date for the spell. |
| `disdate` | Discharge date for the spell. |

### **Admission & Discharge Details**
| Column | Meaning |
|--------|---------|
| `admimeth` | Method of admission (A&E, elective, maternity, etc.). |
| `admisorc` | Source of admission (home, care home, another hospital). |
| `admiage` | Age at admission. |
| `procode` | Provider code (trust). |
| `disdest` | Destination on discharge (home, care home, deceased). |

---

# Hospital Episode Statistics – Outpatients (HES OP)

## Overview
HES OP contains records of **outpatient appointments** in England including:

- First and follow-up appointments  
- Face-to-face & non-face-to-face activity  
- Diagnostic procedures  
- Consultant-led & non-consultant-led care  

## Key Columns in HES OP

### **Identifiers & Demographics**
| Column | Meaning |
|--------|---------|
| `token_person_id` | Pseudonymised patient identifier. |
| `lsoa11` | Geographic location of patient. |

### **Appointment Details**
| Column | Meaning |
|--------|---------|
| `apptdate` | Appointment date. |
| `apptage` | Patient age at appointment. |

### **Provider & Specialty**
| Column | Meaning |
|--------|---------|
| `procode3` | Provider code (3-character version). |
| `tretspef` | Treatment specialty. |

### **Clinical Information**
| Column | Meaning |
|--------|---------|
| `diag_{1–12}` | ICD-10 diagnoses recorded for the appointment. |
| `noprocs` | Number of procedures conducted. |

---

# References
* [ECDS](https://digital.nhs.uk/data-and-information/data-collections-and-data-sets/data-sets/emergency-care-data-set-ecds)
* [HES Technical Output Specification](https://digital.nhs.uk/data-and-information/data-tools-and-services/data-services/hospital-episode-statistics/hospital-episode-statistics-data-dictionary)
