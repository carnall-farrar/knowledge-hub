# Glossary

* **NHS**, National Health Service
* **CDS**, Commissioning Data Sets: The raw format of care activity data submitted by providers to NHS Digital. Includes detailed clinical and administrative data for secondary care. Forms the basis for data flows into SUS and eventually HES.
* **HES**, Hospital Episode Statistics - comprehensive records of patient admissions, outpatient appointments, and A&E visits. HES is a data product created from data submitted to NHS England as part of the Commissioning Data Sets (CDS) managed by the Secondary Uses Service (SUS+). HES is a snapshot of this data at pre-arranged dates during the financial year. HES  is available in 4 datasets:
  * HES APC (01/04/1989 ongoing) (episode level)
  * HES Critical Care (01/04/2007 ongoing)
  * HES OP (01/04/2003 ongoing) (appointment level)
  * HES A&E (01/04/2007 to 01/04/2020) (ecds - event level)
* **ECDS**, Emergency Care Data Set (A&E is 95% of ECDS, 4% is minor injuries, 1% other). The data set containing details of all A&E attendances at NHS hospitals in England, including minor injury units and NHS walk-in centres, as well as 24 hour and consultant-led emergency departments. The ECDS will eventually replace the Hospital Episodes Statistics Accident and Emergency (HES A&E) data set. Coverage: 01/10/2017 ongoing
* **APC**, Admitted patient care. (elective [planned], non-elective [emergency care], maternity spells [typically ignored in our analyses]). If you ever find an abnormally high count of APC spells, it’s likely just a sequence of OP appointments.
* **CC**, Critical Care
* **OP**, Outpatient (appointments/procedures). Planned e.g going in to see a consultant, diagnostic testing. Different from day case (admitted and discharged on the same day)
* **IP**, Inpatient. Inpatient care involves staying overnight in a hospital for medical treatment, while outpatient care provides treatment without requiring an overnight stay. Inpatient care is typically used for serious conditions or complex procedures that require continuous monitoring, whereas outpatient care is often for less severe illnesses or procedures that can be managed with shorter-term appointments. Same thing as APC, but APC is specific terminology used in healthcare data collection.
* **MHDS**, Mental Health Data Set (Typically pretty bad)
* **CSDS**, Community Services Data Set (Typically pretty bad)
* **MSDS**, Maternity Services Data Set
* **DIDS**, Diagnostic Imaging Data Set
* **UEC**, Urgent and Emergency Care
* **ICS**, Integrated Care System
* **ICB**, Integrated Care Board
* **SUS**, Secondary Uses Service - a key data warehouse for hospital activity hosted by the NHS England. Data products like HES, ECDS, MHDS are created from SUS+. It ingests data from the CDS (Commissioning Data Sets) and other sources.
* **UDAL**, The Unified Data Access Layer (UDAL) is the NHS’ main analytical environment. It is a secure de-identified environment, technically and organisationally segregated both from source environments holding identifiable data and from the environment in which pseudonymisation is performed.
* **GPES**, General Practice Extraction Service
* **DWP**, Department for Work & Pensions
* **VPAS**, Voluntary Scheme for Branded Medicines Pricing and Access
* **VPAG**, Voluntary Scheme for Pricing, Access, and Growth
* **DM**+D, Dictionary of Medicines and Devices
* **SNOMED**, Codes (Systematised Nomenclature of Medicine - Clinical Terms): Internationally recognised numeric identifiers for healthcare concepts, providing interoperability and supporting detailed granularity down to specific healthcare terms. Unique identifier with information for Product, Strength, NFC, Manufacturing company, pack size
* **BNF**, Codes (British National Formulary Codes): Structured codes used in NHS prescribing and reporting systems, offering a higher-level granularity linked to categories of medicines for practical clinical use. Unique identifier with information for Product, Strength, NFC
* **IQVIA**, (formerly Quintiles and IMS Health) is a major global player in the pharmaceutical and life sciences sectors. Major business areas are as a CRO (contact research organisation) which is contracted to conduct clinical trials. It also provides data & analytics services, and consulting services pertaining to regulatory compliance, commercial strategy, and market entry.
* **CRO**, Contract Research Organisation
* **ABPI**, the Association of the British Pharmaceutical Industry, is a trade association representing pharmaceutical companies in the UK. It works to ensure that the UK is a leading location for research, development, and use of medicines and vaccines. The ABPI's key areas of focus include improving access to new medicines, fostering a thriving environment for drug discovery, and maintaining high ethical standards. 
* **LOE**, Loss of Exclusivity
* **DHSC**, the Department of Health and Social Care. Doesn’t collect raw health data (that’s done by NHS Digital and other agencies). But it does use and publish data on health and care policy (statistics on NHS performance, waiting times and workforce numbers, funding allocations), Public health data (COVID-19 response and vaccination tracking, health inequalities and social determinants of health), Social care data (care home statistics, adult social care workforce and expenditure), Health economics and spending (budget reports, drug pricing and reimbursement data, NHS capital investment)
* **UKHSA**, UK Health Security Agency
* **ONS**, Office for national statistics
* **MHRA**,Medicines and Healthcare Products Regulatory Agency
* **EMA**, European Medicines Agency data source
* **API**, Active pharmaceutical ingredient, responsible for the therapeutic effect of the product
* **VTM**, (Virtual Therapeutic Moiety): medicine’s active substance (e.g., "Paracetamol"), not tied to a specific product or brand.
* **ATC**, Anatomical Therapeutic Chemical classification
* **ATC_2**, second level of the ATC classification, categorising medicines based on their therapeutic use.
* **NFC**, standardised formulation code used within the BNF system for classifying and identifying medicines.
* **NENC**, Northeast North Cumbria ICS
* **DRG**, Diagnosis Related Group. The DRG coding system is a patient classification scheme used in hospitals to categorise patients into groups based on their primary diagnosis, procedures, and other factors. This system helps to streamline care classifications for billing, especially for Medicare and other insurance companies. DRGs are used to determine reimbursement rates for hospital stays, with hospitals receiving a fixed payment for each DRG, regardless of the actual cost of care. 
* **BOB**, Buckinghamshire, Oxfordshire and Berkshire West ICS
* **TVS**, Thames Valley and Surrey dataset/SDE
* **CMAP**,?
* **DWP**, Department for work and pensions
* **GP**, General Practitioner 
* **NHSE**, NHS England
* **EMIS**, the software/system GPs use to collect and record primary care data
* **RTT**, Referral to Treatment. RTT Pathways  are the routes patients take when referred for specialist treatment by a GP or other healthcare professionals
* **UTLA**, Upper Tier Local Authority (a geographical classification). In England and Wales, UTLAs are the highest level of local govt, including county councils, metropolitan districts, London boroughs, and unitary authorities. In London, the UTLAs are the 32 boroughs and the City of London. 
  **  *** England: 152 total UTLAs - 59 unitary authorities, 36 metropolitan districts, 33 London boroughs (including the City of London), and 24 counties
  **  *** Wales: 22 UTLAs - all unitary authorities so also LTLAs
* **LTLA**, Lower Tier Local Authority:  In the UK it is the lowest level of local government in England and Wales. The UK has a tiered system of local government. LTLA's are at the bottom of this hierarchy, providing the most direct local services to residents. 
* **LSOA**, Lower layer Super Output Area: formed by grouping together several OAs (usually four or five). They are designed to provide more reliable statistical analysis than using OAs alone, especially for smaller areas. Typically contain between 400 and 1,200 households. 
* **OA**, Output Area: the smallest level of geographical unit for census statistics in the UK, created after the 2001 census. 
* **MSOA**, Middle Layer Super Output Area: created by grouping LSOAs together, usually four or five, and are larger than LSOAs, typically containing between 2,000 and 6,000 households. 
* **TDA**, Technical Data Analyst
* **FDP**, Federated Data Platform
* **PHM**, Population Health Management
* **FCE**, Finished Consultant Episodes
* **HCRU**, Healthcare Resource Utilisation
* **ICD**-10, ICD-11, International Classification of Diseases (now International Statistical Classification of Diseases and Related Health Problems)
* **CHI**, Council for Health Insurance (SAUDI)
* **BD**, Business Development
* **PPPH**,?
* **ACT**, (Actual cost of drug or medical device): adjusted cost in GBP after accounting for discounts and additional payments to the dispenser.
* **NIC**, (Net Ingredient Cost of drug or medical device): basic price in GBP of the prescribed drug or appliance, based on Drug Tariff or supplier prices.
* **CU**, (Counting Units): total quantity of a drug or appliance prescribed, calculated as the product of quantity and items.
* **EPD**, (English Prescribing Dataset) - information on all medicines prescribed and dispensed in England in primary care
* **SCMD**, (Secondary Care Medicines Dataset) - prescribing and dispensing information for medicines used within secondary care
* **HPDC**, (Hospital Prescribing Dispensing Community) - medicines prescribed within hospital settings and subsequently dispensed in the community
* **PLIC**, patient-level costs
* **HRG**, Healthcare Resource Group
* **MFF**, market forces factor
* **ACCO**, Alternative Consolidated Contingency
* **NCCI**, National Cost Collection Index
* **IG**, Information Governance
* **RWE**, Real World Evidence - refers to clinical evidence about the usage, benefits, and risks of a medical product that is gathered outside of traditional clinical trials. It is based on RWD. It is used by drug regulators to support approvals and expansions, by Pharma companies to demonstrate the value of products, helps detect long-term and rare adverse effects, can identify treatment-group combinations for personalised medicine.
* **RWD**, real world data - data collected from real-life patient experiences rather than controlled trial environments. Data sources include electronic health records (EHR), insurance data, patient registries, wearable biotech and health apps, patient-reported outcomes, pharmacy and prescription data.
* **EHR**, Electronic health records e.g EMIS
* **SDE**, Secure Data Environment - Researchers access data within secure platforms, ensuring data does not leave the environment
* **DARS**, Data Access Request Service - Centralised service for applying to access health and social care data from the NHS
* **HRA**, Health Research Authority
* **MHSDS**, Mental Health Services Data Set - Captures information on people in contact with mental health services
* **OPCRD**, Optimum Patient Care Research Database - Contains de-identified data from primary medical records across the UK
* **CPRD**, Clinical Practice Research Datalink - Provides anonymised primary care records for research
* **ASCOF**, Adult Social Care Outcomes Framework - Measures how well care services achieve outcomes
* **NIMS**, National Immunisation Management System - Tracks vaccination records
* **NHSBSA**, NHS Business Services Authority - Custodian of prescribing and medicines data
* **PCA**, Prescription Cost Analysis - Dataset providing details on prescriptions dispensed in the community
* **MH**, Mental Health
* **MSK**, musculoskeletal. MSK surgery focuses on treating conditions affecting the muscles, bones, joints, and related tissues.
* **PAH**, Pulmonary Hypertension
* **PCN**, Patient Care Network
* **ISO**, International Organisation for Standardisation. ISO accreditation in the UK is the formal recognition of a certification body's competence to conduct ISO certification audits, ensuring that they meet the highest standards of reliability and impartiality. It's essentially a "seal of approval" from the UK Accreditation Service (UKAS) or a similar body, confirming that the certification body is qualified to issue ISO certifications. 
* **DSA**, Data Subject Access request
* **DPIA**, Data Protection Impact Assessment: a process used to identify and minimise data protection risks associated with a project or plan. It's a key part of demonstrating compliance with data protection laws like the UK GDPR and ensures you've considered the impact of processing personal data
* **USP**, Unique Selling Proposition: the essence of what makes your product or service better than competitors. In online marketing, communicating your USP clearly and quickly is one of the keys to getting potential customers to convert on your site.
* **MFT**, Managed File Transfer or Manchester Frimley Trust 
* **PLICS**, Patient Level Information and Costing System Data Collection
* **CTP**, NHS England's Costing Transformation Programme was set up to implement PLICS across acute, mental health, ambulance and community providers.
* **AC**, Acute Care refers to short–term treatment, usually in a hospital, for patients with any kind of physical or mental health illness or injury. Acute NHS Trusts provide services such as accident and emergency departments, inpatient and outpatient medicine and surgery and in some cases very specialist medical care.
* **Multi**-morbidity refers to the presence of two or more long-term health conditions in an individual. It's a common phenomenon, especially in older populations, and can significantly impact an individual's health and quality of life. Common examples include the co-existence of diabetes and cardiovascular disease, or the combination of mental health conditions like depression and physical conditions like chronic pain. 
* **QALY**, Quality-Adjusted Life Years: QALYs are an attempt to take into account both length of life and the quality of life. QALYs are increasingly used in debates on the economic impacts of health for two reasons. First, they are a way of comparing the outcomes of many different types of illness, treatments for illness and attempts to prevent it – including the social determinants of health – and are therefore a good metric to help decision-makers choose between options. They are therefore commonly used in ‘cost per QALY’ studies of cost-effectiveness analysis. Second, there are existing estimates of how much the population is actually willing to pay (or fund through taxation) for the health improvements that a QALY confers. It is therefore possible to translate QALY gains into monetary equivalents. This valuation of a QALY provides a useful indicator for determining the cost threshold for public health interventions on the social determinants of health.
* **NICE**, National Institute for Health and Care Excellence: evidence-based guidance and health technology appraisal
* **LTC**, Long-Term Condition
* **SMI**, Severe Mental Illness
* **CVD**, Cardiovascular Disease
* **CVDRM**, Cardiovascular Disease Risk Management
* **WSIC**, Whole Systems Integrated Care: It refers to a system where health and social care services work together to provide a person-centered, integrated approach to care. This means that care is coordinated across different agencies, and individuals receive support based on their needs, goals, and preferences. There is a similarly named dataset created by the NorthWest London ICS which includes their own PHM segmentation heuristic.
* **B2H**, Bridges to Health: The National B2H dataset has been developed by OBH in partnership with NHS England, for the purposes of supporting PHM. The dataset is derived from 10 different data sources available in the National Commissioning Data Repository; these include MPI, SUS, ECDS, CSDS and MHSDS, but excludes primary care data. The register of 59 clinical conditions has been curated by a team of clinicians, data analysts, and public health experts. 8 years of data are included, until March 2024.
* **OBH**, Outcomes Based Healthcare
* **GM**, Greater Manchester. NHS GM is the ICB for the area. The ICB created a linked dataset combining secondary and primary care data in the Advance Data Science Platform (ADSP). With this linked dataset they created a B2H-inspired population segmentation for PHM. Their segmentation includes age band (3 bands: 0-17, 18-64, 65+) as a second dimension.
* **ADSP**, Advance Data Science Platform
* **HbA1c**, is your average blood glucose (sugar) levels for the last two to three months. Used to diagnose and monitor diabetes
* **IMD**, Index of Multiple Deprivation: the official rank of relative deprivation for small areas in the UK. It ranks every small area from 1 (most deprived) to the least deprived. Typically reported in deciles. The statistical unit areas used to provide indices of relative deprivation across the country are Lower layer Super Output Areas (LSOAs) [England, Wales], Data Zones [Scotland] and Super Output Areas or Wards [Northern Ireland].
* **ETOS**, Enhanced Technical Output Specification
* **CQC**, Care Quality Commission
* **VCSE**, Voluntary Community and Social Enterprises
* **CMI**, Chartered Management Institute
* **HRG**, Health Resource Group
* **OBD**, Occupied Bed Day
* **IBD**, Inflammatory bowel disease
* **IBS**, Irritable bowel syndrome
* **HPM**, Health partnership managers. People in ABBVIE who are door-to-door selling products. Used the ABBVIE data to inform who to go bug
* **ACO**, Accountable care organisation
* **CCG**, Clinical Commissioning Group
* **CIP**, Cost Improvement Plans​
* **CSU**, Commissioning Support Unit​
* **FOI**, Freedom of Information
* **LTP**, Long term plan
* **HEE**, Health Education England
* **WTE**, Whole Time Equivalent
* **HWB**, Health and wellbeing board​
* **LA**, Local Authority
* **QOF**, Quality Outcome Framework​
* **VCSE**, Voluntary, community, and social enterprise​
* **OOH**, Out of hours / hospital​
* **PbR**, Payment by results
* **SRO**, Senior Responsible Owner​
* **PHE**, Public Health England​
* **QIPP**, Quality, Innovation, Productivity and Prevention​
* **CAMHS**, Child and Adolescent Mental Health services
* **VCR**, Vaccination Coverage Rate
* **SpR**, Specialty Registrar

## External Resources
- [The King's Fund - Health and Care Defined Jargon Buster](https://www.kingsfund.org.uk/insight-and-analysis/articles/health-and-care-defined-jargon-buster)
