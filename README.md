# Choosing Immune Suppression in Renal Transplantation by Efficacy and Morbidity (CISTEM2) 

Funding agency: NIH/NIDDK <br/>
Funding period: TBD <br/>
PI: Vikas Dharnidharka, MD (WashU); David Axelrod, MD (UIowa) <br/>
Co-PI/Co-I: Xing Song (MU) <br/>
GROUSE Cohort: Weight <br/>
Data Access Type: GROUSE, CMS-only <br/>
GPC DROC request:  <br/>

# Study Overview 

Recognizing the data continuum gaps in CISTEM [e.g., lack of longitudinal information on more granular clinical observations and outcome measures, such as serum creatinine levels (for computation of estimated glomerular filtration rate, eGFR), tacrolimus drug levels, measures of viremia and viuria, biopsy reports (for defining acute rejection (AR) and other forms of graft injury), malignancy diagnoses, rehospitalization events], we will establish a novel, robust and curated database (CISTEM2 database) integrating transplant registry data with multi-site electronic medical records (EMRs), administrative claims, and social determinants of health data for renal transplant patients leveraging the PCORnet infrastructure.  

# Site Scope of Work 

The GPC Coordinating Center (GCC) located at University of Missouri will operate as the data linkage and integration hub (DLIH).   

## Contracting and Regulatory 

### 1) Institutional Review Board 

The leading site (WASHU) will obtain a master IRB (with HIPAA waiver) to govern the study. Given that the nature of the project is using Datavant technology to generate de-identified hash token which will be shared with GCC and there is no way for GCC to re-identify the individuals, this project may be determined as non-human-subject (NHS) project by your local IRB. For sites that would require an IRB, we will leverage the Smart IRB system for IRB reliance to the master IRB. For sites determined as NHS, please submit the NHS determination letter to the leading IRB site. 

### 2) Data Transfer and Use Agreement 

A CISTEM2 study-specific Data Transfer and User Agreement (DTUA), in line with the master GPC Data Sharing Agreement (DSA), will be developed, reviewed and signed by interested study sites. Both Scientific Registry of Transplant Recipient (SRTR) registry and the approved study sites will forward hashes to the DLIH at GCC, where data linkage and integration will be performed. For overlapped patients, the honest broker at GCC will request GPC EHR data in CDM format following the GPC Data-as-a-Product (DaaP) model. Separate DUAs have been established between leading site and SRTR and USRDS. A new CMS DUA will be further established between the leading site and CMS for Medicare Advantage data request.    

### 3) Datavant License Agreements and Order Forms 

The Datavant corporation is not serving the Honest Broker for CISTEM2 SRTR-GPC linkage. However, utilization of the Datavant software is necessary to create tokens to be linked across CISTEM2 data sources. All PCORnet sites have an existing Site License Agreement (SLA) in place with Datavant and already have access to the Datavant De-ID software. To supplement the extant Site License Agreement, a CISTEM2 study-specific Order Form will be provided by Datavant to request basic details about the SLA at your site, such as the license number. This is a NO COST, NO SIGNATURE FORM that must be returned to the GCC and the contact at Datavant regardless of who serves as the Honest Broker. There is no cost to your site to utilize Datavant software for the purposes of CISTEM2. 

# Data Linkage and Integration Workflow  

### 1) Utilization of Datavant Software 

The Datavant software solution enables Privacy-Preserving-Record Linkage (PPRL) through the use of de-identified, encrypted tokens that can be linked across data sources. CISTEM2 sites with existing SLAs have already installed the Datavant De-ID software to generate multiple, encrypted identifiers (hash tokens) based on different permutations of personally identifiable information (PII) held within source systems. SRTR has also installed this software. The underlying PII is processed by the Datavant De-ID software, where it is irreversibly hashed (i.e., cannot regenerate the PII from the hash value) into a series of Master Tokens using the Datavant Master Seed. The key-based hashing process means that the same PII processed at one site will result in different hashes from those produced from another site. In order to match tokens from different sites, the site-specific Master Tokens are then transformed into Transit tokens that are specifically directed at a third-party site using a site-specific key. This means that if the transit tokens are accidentally sent to the wrong location, the transit tokens cannot be processed by the incorrect site. The receiving site can then transform the transit tokens from different sites into tokens that can be used to match the same patients across different sites. The same PII always generates the same set of Master Tokens, but it is never present in any output or log stream from the De-ID software. Only the site-specific encryption tokens are written to the output file. 

### 2) Tokenization and CISTEM2 Cohort Identification

Add FIGURE. CISTEM2 cohort includes all kidney transplant (Kx) patients who are included in the SRTR registry with an established linkage between SRTR registry and USRDS database. As shown in Figure 1, GCC will first leverage Datavant linkage to identify the crosswalk population between GPC EHR cohort and SRTR registry to generate site-specific finder files. The finder files will then be disseminated to participating sites for clinical data extraction (i.e., CDM-CISTEM2) on the crosswalk Kx patients.  

### 3) CDM Data Submission 

The CISTEM2 database will be established on the GCC cloud-based data infrastructure leveraging Amazon Web Services (AWS) services and Snowflake Data cloud technologies. GCC will utilize AWS S3 bucket for data transfer and storage. GCC will create separate S3 bucket for each participating site and site-specific role with “lease privileges” so that it can only access site-specific bucket. Each extracted CDM-CISTEM2 clinical dataset will be submitted to these site-specific AWS S3 buckets following the TLS/SSL secure protocol. Participating sites can also choose to adopt additional layer of data encryption following AES-256 with password protection.    

### 4) Data Integration  

Upon receiving data from participating sites, SRTR, USRDS and CMS. GCC will perform data linkage and integration using the mapping among four source-specific, masked identifiers: PATID, HASH_ID, OPTN_HID, and BENE_ID.  HASH_ID is the study-specific transit token generated by Datavant software.   
