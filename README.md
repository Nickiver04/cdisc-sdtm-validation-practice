# CDISC SDTM Data Validation Practice

## About This Project
This project documents my hands-on practice with CDISC data standards 
and SDTM data validation as part of my preparation for a Clinical Data 
Associate role. It is based on completing the CDISC Pediatrics User 
Guide v1.0 online training followed by independent practice using 
Pinnacle 21 Community.


## Training Completed
**CDISC Pediatrics User Guide v1.0 Online Training**
Offered by JWMDRC in collaboration with CDISC

Topics covered:
- Introduction to CDISC, CDASH and SDTM
- SDTM domain structure, variable naming conventions and observation classes
- CDASH to SDTM mapping and transformation
- Pediatrics-specific standards: age types, nutrition, auricular assessments,
  consent and assent, questionnaires and associated persons


## Tools Used
- Pinnacle 21 Community v4.1.0
- Validation Engine: FDA 2508.1
- CDISC SDTM CT Version: 2025-03-28
- Dataset source: cdiscdataset.com (synthetic SDTM datasets)



## Datasets Validated

| Domain | Label              | Records |
|--------|--------------------|---------|
| AE     | Adverse Events     | 118     |
| DM     | Demographics       | 100     |
| DS     | Disposition        | 250     |
| LB     | Laboratory Tests   | 4,500   |
| MH     | Medical History    | 84      |
| VS     | Vital Signs        | 2,250   |
| SE     | Subject Elements   | 150     |
| HO     | Healthcare Encounters | 9    |
| **Total** |                 | **7,461** |



## Key Validation Errors Identified

| Error ID | Domain | Issue | Records |
|----------|--------|-------|---------|
| SD1334 | DM | Informed consent date after first dose date | 51 |
| SD1240 | DM/DS | Missing informed consent record in DS | 100 |
| SD2288 | DM | No disposition event record found | 100 |
| SD0009 | AE | Serious AE with no seriousness criterion | 2 |
| SD1011 | AE | Invalid ISO 8601 duration format in AEDUR | 85 |
| SD1254 | AE/DM | Death flag inconsistency across domains | 20 |
| SD1332 | AE | Ongoing AE has end date populated | 29 |
| SD1333 | AE | Recovered AE missing end date | 17 |
| SD2236 | DM | Actual arm does not match planned arm | 5 |
| SD1457 | GLOBAL | Invalid dataset filename format | 1 |

Full error analysis with clinical interpretation available in 
reports/error-analysis.xlsx



## What I Learned

**SDTM Structure**
- Data is organized into domains — each a separate .xpt file
- Variables follow a naming convention: domain prefix + topic + suffix
- USUBJID links every subject's data across all domains

**Critical Regulatory Rules**
- Informed consent date must always precede first dose date
- Serious AEs must have at least one seriousness criterion documented
- Duration variables must follow ISO 8601 format (P142D not 142)
- Cross-domain consistency is validated — AE and DM death data must match
- Dataset files must be named exactly after their 2-letter domain code

**CDASH vs SDTM**
- CDASH = how data is collected on CRFs (human friendly)
- SDTM = how data is submitted to regulators (machine readable)
- Key differences: ISO date format, derived variables, controlled terminology



## References
- CDISC SDTM Implementation Guide — cdisc.org
- Pinnacle 21 Community — pinnacle21.certara.net
- CDISC Pediatrics User Guide v1.0 — jwmdrc.org
- FDA Study Data Standards — fda.gov


## Author
Fresher CDA candidate | Open to Clinical Data Associate / 
Clinical Data Coordinator opportunities
