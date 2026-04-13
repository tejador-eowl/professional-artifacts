# JIT Secure AI Inference: PII Data Protection

This project demonstrates a **Zero-Trust** architectural pattern for protecting sensitive PII during Generative AI (GenAI) inference. By combining **Thales CipherTrust Application Data Protection** with **Google BigQuery**, we ensure data remains encrypted throughout its cloud lifecycle and is only decrypted "Just-in-Time" for authorized users.

## Key Features
- **Persistent Encryption:** Data is encrypted on-prem using Thales Batch Data Transformation (BDT) before cloud migration.
- **Just-in-Time (JIT) Decryption:** Leverages BigQuery User Defined Functions (UDFs) to call the CipherTrust RESTful API dynamically.
- **Zero-Trust Alignment:** Minimizes the blast radius of data exposure by ensuring nonpublic clear-text data is never stored in the cloud.
- **Compliance Ready:** Designed to meet NIST and CISA guidance for safe and trustworthy AI.

##  Architecture Overview
1. **Source:** On-prem relational database containing sensitive PII.
2. **Transformation:** Thales BDT encrypts fields before landing in **Google Cloud Storage**.
3. **Storage:** Data is loaded into **Google BigQuery** as encrypted strings.
4. **Inference:** A GenAI model queries the data via a **BigQuery UDF**. 
5. **Policy Check:** The UDF triggers a REST call to the **CipherTrust Manager**; decryption only occurs if the caller has the appropriate policy/token.

##  Project Artifacts
- `/scripts`: Sample SQL for BigQuery UDF configuration.
- `/docs`: Detailed architectural diagrams and policy templates.
- `/demos`: Links to the video walkthrough and summary materials.

##  Stakeholders
- **CISO/CIO:** Risk mitigation and regulatory compliance (GDPR, CCPA).
- **InfoSec Managers:** Policy enforcement and key management.
- **Data Engineers:** Efficient, scalable encryption/decryption pipelines.
