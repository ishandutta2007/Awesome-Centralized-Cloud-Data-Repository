# Awesome-Centralized-Cloud-Data-Repository

# Awesome-Centralized-Cloud-Data-Repository

**Top Centralized Cloud Data Repository (Opensource) 🌟 Star if you like it! 🌟**



**Curated List of SaaS Products & Open-Source GitHub Projects**

*Focused on Data Catalogs, Lakehouse Governance, Object Storage & Open Table Formats*

**Last updated: October 2026**



This repository tracks notable **SaaS platforms** and **open-source projects** for **Centralized Cloud Data Repositories**. These tools enable organizations to unify data across warehouses, lakes, and object storage—providing a single catalog, consistent access control, and shared metadata—from fully managed governance platforms with credential vending and lineage tracking to open-source catalogs and S3-compatible storage that give teams complete control over their data estate.



**Examples** include Databricks Unity Catalog, Snowflake Secure Data Sharing, AWS Lake Formation, Google Cloud Dataplex, Microsoft Purview, Cloudera SDX, Dremio Arctic, Apache Iceberg, MinIO, and NetApp StorageGRID (the category leaders in commercial and open-source space).



**Open-source emphasis**: This section is expanded with every relevant project for self-hosted catalogs, object storage, and open lakehouse infrastructure. **Critical note**: The open-source data repository landscape is genuinely active—**Apache Iceberg** has become the de facto open table format, **MinIO** provides S3-compatible object storage, and **Apache Polaris** and **Nessie** offer open catalog implementations. No open-source project matches Unity Catalog's unified governance across tables, volumes, and ML models at enterprise scale, but the foundational layers are mature and production-proven.



Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.



## Table of Contents

- [SaaS/Hosted Platforms](#saas-hosted-platforms)

- [Open-Source GitHub Projects](#open-source-github-projects)

- [How to Contribute](#how-to-contribute)

- [Disclaimer](#disclaimer)



## SaaS/Hosted Platforms



- **[Databricks Unity Catalog](https://www.databricks.com/)**

  **Unified governance layer for data and AI** across the lakehouse. In production since 2021, managing **~100 million tables, ~550,000 volumes, and ~400,000 ML models** for ~9,000 customers, serving ~60,000 API calls per second . **Features**: Three-level namespace (catalog.schema.object); **credential vending**—clients never access cloud storage directly; UC issues temporary credentials after enforcing access policies; **catalog federation** to mount external catalogs (HMS, on-prem DBMS); **Delta UniForm** for Iceberg/Hudi interoperability; lineage APIs; change event streams for discovery catalogs; audit log system tables . **Pricing**: Quote-only; bundled with Databricks platform. **Free tier**: Limited Community Edition. **Best for**: Databricks customers wanting unified governance across tables, volumes, models, and AI assets—**trade-off**: ecosystem lock-in and enterprise pricing.



- **[Snowflake Secure Data Sharing](https://www.snowflake.com/)**

  **Cross-account data sharing without data copying** using Snowflake's services layer and metadata store. **No actual data is replicated or transferred**—shared objects are read-only, and consumers pay only for compute to query them . Supports tables, dynamic tables, external tables, Iceberg tables, views, UDFs, and models. **Reader accounts** enable sharing with parties who do not have Snowflake licenses . **Architecture**: Multi-cluster, shared-data—storage (S3), virtual warehouses (compute), and cloud services (metadata, access control, optimization) are separated . **Pricing**: Consumption-based credits; no storage cost to consumers for shared data. **Free tier**: Trial credits available. **Best for**: Snowflake customers wanting governed data sharing across business units, partners, or customers without ETL or data duplication.



- **[AWS Lake Formation](https://aws.amazon.com/lake-formation/)**

  **Data lake governance** built on AWS Glue Data Catalog. **No additional charge** for Lake Formation features—standard rates apply for underlying S3, Glue, and compute services . Centralizes permissions across S3, Athena, EMR, Redshift, and other AWS analytics services. **Pricing**: No Lake Formation surcharge; pay for AWS services consumed. **Free tier**: AWS Free Tier applies to underlying services. **Best for**: AWS-centric organizations wanting centralized access control for S3-based data lakes without additional governance licensing.



- **[Google Cloud Dataplex](https://cloud.google.com/dataplex)**

  **Intelligent data fabric** for unified analytics across distributed data. Introduces **Lakes** (logical data domains) and **Zones** (sub-domains for data contracts and security), with policies propagating from Lakes to Zones to assets . **Automated metadata discovery** for structured and unstructured data; **sensitive data classification**; data quality checks and anomaly detection. **Pricing**: Consumption-based on Google Cloud; no separate onboarding fees for platform access . **Free tier**: Google Cloud Free Tier applies. **Best for**: Google Cloud organizations wanting automated metadata management and centralized governance across BigQuery, Dataproc, and GCS.



- **[Microsoft Purview](https://www.microsoft.com/en-us/security/business/microsoft-purview)**

  **Unified data governance, risk, and compliance** platform spanning M365, Azure, and hybrid sources. Includes Data Catalog, sensitivity labels, DLP, Insider Risk Management, eDiscovery, and Compliance Manager . **Critical for M365 Copilot**—sensitivity labels and DLP prevent Copilot from exposing over-shared content to unauthorized users . **Pricing**: Requires M365 E5 Compliance add-on (**$12/user/month**) or full E5 (**$57/user/month**) for complete functionality . **Free tier**: Basic labels and DLP on E3. **Best for**: Microsoft 365 enterprises needing governance that covers both data catalog and information protection—**trade-off**: licensing cost and Microsoft ecosystem focus.



- **[Cloudera Shared Data Experience (SDX)](https://www.cloudera.com/)**

  **Unified data access and governance** across Cloudera environments. Integration with **Trino** and **Octopai Data Lineage** delivers a single secure endpoint for all data across engines, clouds, and on-premises without duplicating security policies . Unifies metadata and access controls for self-service data access. **Pricing**: Quote-only; bundled with Cloudera Data Platform. **Free tier**: None. **Best for**: Cloudera CDP customers wanting centralized governance across hybrid data estates.



- **[Dremio Arctic](https://www.dremio.com/)**

  **Data lakehouse management service** with Git-like operations for Apache Iceberg catalogs. Built on **Project Nessie**—provides branching, version control, and rollback for datasets without copying data . Works with Dremio Sonar, Apache Spark, and Apache Flink. **Pricing**: Quote-only; bundled with Dremio Cloud. **Free tier**: Trial available. **Best for**: teams wanting version-controlled Iceberg catalogs with Git-like workflows for data experimentation and audit.



## Open-Source GitHub Projects



- **[Apache Iceberg](https://github.com/apache/iceberg)**

  **Open table format for huge analytic tables** (Apache 2.0, ~8,620 stars) — **the de facto standard for open lakehouse table storage**, enabling engines like Spark, Trino, Flink, and Snowflake to safely work with the same tables concurrently . **Features**: **Hidden partitioning** and partition evolution without rewriting data; **snapshot isolation** with ACID guarantees; **schema evolution** (add, drop, rename, reorder columns); time travel queries; supports Parquet, ORC, and Avro file formats. **Tech stack**: Java (core), Python. **Deploy**: Integrated with compute engines; catalogs provided separately (Polaris, Nessie, HMS). **Trade-off**: **Table format specification, not a catalog or storage layer**—it defines how tables are structured; you still need a catalog (Polaris/Nessie) and storage (S3/MinIO). **Best for**: organizations building open lakehouse architectures wanting vendor-neutral table storage that multiple engines can access simultaneously—the foundation of any open centralized data repository.



- **[MinIO](https://github.com/minio/minio)**

  **High-performance, S3-compatible object storage** (AGPL-3.0) — **the most widely deployed open-source object storage server** for cloud-native data repositories . **Features**: **Fully S3-compatible API**—works with existing SDKs, tools, and automation; **erasure coding and bitrot protection** for data reliability; **distributed deployment** with horizontal scaling; **encryption** (TLS/HTTPS) with access keys and LDAP/AD identity integration; **single binary** deployment on Linux, Docker, Kubernetes; built-in web console . **Tech stack**: Go. **Deploy**: Self-hosted (binary, Docker, Kubernetes). **Trade-off**: **Object storage only**—it provides S3-compatible buckets, not a data catalog, governance layer, or table format. It is the storage foundation that catalogs like Polaris or Nessie manage. **Best for**: teams wanting a self-hosted, S3-compatible object store as the foundation for a data lake—without AWS S3 costs or vendor lock-in.



- **[Apache Polaris](https://github.com/apache/polaris)**

  **Interoperable open-source catalog for Apache Iceberg** (Apache 2.0, ~1,872 stars) — **the leading open catalog implementation** for multi-engine Iceberg access . **Features**: **Iceberg REST Catalog** interface; credential vending; supports multiple compute engines (Spark, Trino, Flink, Dremio); role-based access control; designed for interoperability and vendor neutrality. **Tech stack**: Java. **Deploy**: Self-hosted. **Trade-off**: **Catalog only**—it manages Iceberg table metadata and access; it does not provide storage (use MinIO/S3) or query engines (use Spark/Trino). **Best for**: teams wanting an open, vendor-neutral Iceberg catalog that multiple engines can share—the open-source answer to Unity Catalog's catalog layer.



- **[Project Nessie](https://github.com/projectnessie/nessie)**

  **Transactional catalog for data lakes with Git-like semantics** (Apache 2.0, ~1,430 stars) — **the open-source foundation behind Dremio Arctic** . **Features**: **Git-like branching, commits, merges, and tags** for Iceberg tables; **snapshot isolation** for concurrent writes; **version control** for data experiments and audit; supports multiple table formats; Iceberg REST Catalog compatibility. **Tech stack**: Java. **Deploy**: Self-hosted. **Trade-off**: **Catalog with versioning focus**—adds Git-like workflows on top of Iceberg; not a governance platform with fine-grained access policies like Polaris or Unity Catalog. **Best for**: data teams wanting version-controlled Iceberg catalogs for experimentation, rollback, and audit—especially those already using Dremio Arctic or wanting Git-like data workflows.



- **[Apache Gravitino](https://github.com/apache/gravitino)**

  **Open data catalog for building high-performance, geo-distributed, federated metadata lakes** (Apache 2.0, ~2,905 stars) — **the most ambitious open-source catalog project** in scope, supporting multiple metadata sources . **Features**: **Federated metadata** across Hive, Iceberg, Hudi, Kafka, and relational databases; **geo-distributed** architecture; unified API for metadata access; supports multiple table formats. **Tech stack**: Java. **Deploy**: Self-hosted. **Trade-off**: **Catalog federation, not storage or query**—it unifies metadata from existing catalogs; it does not replace them. Newer project with growing but limited production validation compared to Polaris or Nessie. **Best for**: organizations with heterogeneous metadata sources wanting a federated catalog layer without migrating everything to one format.



- **[LinkedIn OpenHouse](https://github.com/linkedin/openhouse)**

  **Open control plane for tables in the data lakehouse** (Apache 2.0, ~381 stars) — **LinkedIn's production catalog for Iceberg tables** . **Features**: **Table lifecycle management** (create, delete, optimize); **declarative table management**; **data layout optimization**; built for Iceberg tables at scale; serves as the control plane for LinkedIn's lakehouse. **Tech stack**: Java. **Deploy**: Self-hosted. **Trade-off**: **Control plane, not a general catalog**—focused on Iceberg table operations; smaller community than Polaris or Nessie. **Best for**: organizations running Iceberg at scale wanting a proven control plane for table lifecycle and optimization—especially those inspired by LinkedIn's lakehouse architecture.



### Additional Strong Open-Source Options



- **Apache Hudi** — Open data lake platform with upserts and incremental processing (Apache 2.0). **Note**: Table format alternative to Iceberg with stronger upsert/CDC focus; not a catalog or storage layer. **Best for**: teams needing streaming upserts and incremental ETL on the data lake.

- **Lakekeeper** — Apache-licensed Iceberg REST Catalog in Rust (~1,210 stars). **Note**: Newer catalog implementation; less community validation than Polaris. **Best for**: teams wanting a lightweight, Rust-based Iceberg catalog .

- **Apache Amoro** — Lakehouse management system on open formats (~1,115 stars). **Note**: Management layer, not a full catalog or storage. **Best for**: teams wanting lakehouse optimization and management on Iceberg/Hudi .



**Frameworks for building custom systems**: Combine **MinIO** as S3-compatible storage with **Apache Iceberg** as the table format, **Apache Polaris** or **Project Nessie** as the catalog, and **Apache Gravitino** for federated metadata—creating a fully open-source centralized data repository. **None of these match Unity Catalog's unified governance across tables, volumes, and ML models** or Snowflake's zero-copy sharing, but the foundational layers are mature and production-proven at scale.



## How to Contribute



1. Fork the repo.

2. Add/edit entries in `README.md` (follow existing format).

3. Include: name, link, 1–2 sentence description, license (for open-source), and whether it's SaaS or open-source.

4. Submit PR with a short explanation.



Star the repo if you find it useful!



## Disclaimer



- This is a **community-curated** list — not exhaustive and not an endorsement.

- Centralized data repository platforms handling enterprise data must comply with data protection regulations (GDPR, CCPA, etc.) and implement appropriate access controls, encryption, and audit logging.

- **The "unified governance platform" vs. "catalog" vs. "object storage" vs. "table format" distinction is critical.** **Databricks Unity Catalog, Snowflake Secure Data Sharing, AWS Lake Formation, Dataplex, Purview, Cloudera SDX, and Dremio Arctic** are **platforms**—they combine catalog, governance, and often compute integration. **Apache Polaris, Nessie, Gravitino, and OpenHouse** are **catalogs**—they manage metadata and access but rely on external storage and compute . **MinIO and NetApp StorageGRID** are **object storage**—they provide S3-compatible buckets but no catalog or governance . **Apache Iceberg** is a **table format**—it defines how data files are organized; it is not a catalog or storage layer . **Choose based on whether you need a complete platform, a catalog layer, storage, or a table format.**

- **Apache Iceberg is the foundation of the open-source data repository stack.** It is the de facto open table format, supported by Spark, Trino, Flink, Snowflake, and Databricks . **Without Iceberg, Polaris, Nessie, and MinIO have nothing to catalog or store.**

- **MinIO is the storage layer that makes self-hosted data lakes practical**—S3-compatible, erasure-coded, single-binary deployment . **The trade-off**: it is storage only; you still need a catalog (Polaris/Nessie) and query engine (Spark/Trino).

- **Apache Polaris is the leading open Iceberg catalog** for multi-engine access, with ~1,872 stars and active development . **Project Nessie adds Git-like versioning** on top of Iceberg, powering Dremio Arctic . **Choose Polaris for straightforward multi-engine catalogs; choose Nessie for version-controlled data workflows.**

- **Unity Catalog and Snowflake represent fundamentally different approaches.** Unity Catalog is a **governance layer** that manages tables, volumes, models, and AI assets with credential vending . Snowflake's Secure Data Sharing is a **zero-copy sharing mechanism**—no data is transferred; consumers query the provider's data directly . **Both are powerful but solve different problems**—governance vs. sharing.

- **Microsoft Purview is unique in covering both data catalog and information protection** (DLP, sensitivity labels, insider risk) . **The trade-off**: requires M365 E5 licensing ($12–$57/user/month) and is Microsoft-centric.

- **Pricing opacity varies.** Unity Catalog is bundled with Databricks. Lake Formation has no surcharge . Dataplex is consumption-based on GCP . Purview requires E5 licensing . Snowflake, Cloudera, and Dremio require sales contact. **Validate with direct vendor conversations against your data volume and governance requirements.**

- Self-hosted open-source solutions require proper infrastructure (object storage, catalog services, compute engines), security hardening, and ongoing maintenance. **Data repository infrastructure is business-critical**—ensure your deployment meets your organization's reliability and security requirements before migrating production data.



---



**Made for data engineers, platform teams, and organizations building transparent centralized data repository solutions.**

Let's make Centralized Cloud Data Repositories more open, data-driven, and governance-aware.
