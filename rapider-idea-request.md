<!-- Rapider Official App SOW & Specification | App #099: Data Warehouse & Analytics Platform (data-warehouse) | Domain: DAT -->

# #099 Data Warehouse & Analytics Platform (`data-warehouse`) — Scope of Work (SOW)

- **App Number & Slug:** `#099` / `099-data-warehouse-and-analytics-platform`
- **Proposed Rapider App Key:** `data-warehouse`
- **Suite / Domain Key:** `DAT` (Data, Analytics & Business Intelligence Suite — `Dat*` Canonical Prefix)
- **Representative Product (`P1`):** Snowflake
- **Combined Feature Catalog Reference:** [../combined-features/099-data-warehouse-and-analytics-platform-features.md](../combined-features/099-data-warehouse-and-analytics-platform-features.md)

---

## 1. Executive Outcome & Target Audience

`data-warehouse` provides the elastic analytical SQL compute, open lakehouse storage (`Apache Iceberg` + native columnar), collaborative SQL Worksheet Studio, Time Travel recovery, Zero-Copy Data Sharing, and FinOps cost governance foundation for the entire Rapider `DAT` suite. Traditional analytics databases either couple storage and compute—forcing teams to choose between slow executive dashboards and over-provisioned 24/7 hardware—or suffer from runaway consumption bills caused by unindexed ad-hoc queries. `data-warehouse` decouples catalog storage (`DatDatabaseCatalog`, `DatWarehouseTable`) from workload-isolated elastic compute pools (`DatComputeCluster`) protected by hard FinOps credit & byte-scan guardrails (`DatResourceMonitor`).

- **SME Fast-Path Defaults:** Growing teams get an instant serverless-ready `DEFAULT_ANALYTICS` compute cluster (with 60-second auto-suspend) and pre-mounted zero-copy read shortcuts over canonical Rapider suite collections (`CRM`, `FIN`, `HR`, `OPS`, `SUP`) so analysts can run cross-suite SQL joins in `sql-worksheets` immediately with a default monthly budget cap.
- **Enterprise Progressive Disclosure:** Data architects and FinOps leads provision isolated `ETL_INGEST`, `BI_REPORTING`, and `ADHOC_ANALYST` multi-cluster compute pools, manage open Apache Iceberg tables, clone zero-copy `DEV/QA` sandboxes, recover dropped data via 90-day Time Travel, publish clean-room `DatDataShare` listings approved via Home `WorkItem`s, and attribute compute spend back to `HrDepartment` and `FinBudget`.
- **Measurable Success Outcomes:**
  - Zero compute contention between heavy `#098` ELT batch transformations and live `#096` executive dashboard queries.
  - 100% prevention of runaway warehouse spend via per-statement byte-scan limits (`maxBytesScanned`) and `DatResourceMonitor` auto-suspension thresholds.
  - Instant (`< 5s`) zero-copy schema cloning and point-in-time Time Travel table restoration without duplicating underlying Parquet/Iceberg storage blocks.
- **Top 6 Global Benchmarks Synthesized:** `P1` Snowflake, `P2` Databricks Data Intelligence Platform, `P3` Google BigQuery, `P4` Microsoft Fabric Warehouse, `P5` SAP Datasphere, and `P6` Oracle Autonomous Data Warehouse.

---

## 2. In-Scope, Out-of-Scope & Suite Ownership Boundaries

### In-Scope
1. Hierarchical database/schema catalogs (`DatDatabaseCatalog`), managed columnar + open Apache Iceberg tables, dynamic/materialized views, zero-copy canonical Rapider suite shortcuts, shallow clones, and Time Travel (`DatWarehouseTable`).
2. Elastic workload-isolated compute clusters (`DatComputeCluster`) with T-shirt sizing (`XS`–`4XL`), auto-suspend/auto-resume, multi-cluster concurrency autoscaling, and per-query timeout/byte-scan caps.
3. Collaborative SQL Worksheet Studio (`DatSavedSqlWorksheet`) with schema autocomplete, cost dry-run estimation, visual operator-level query execution plans (`DatQueryExecution`), and grounded SQL Copilot.
4. FinOps resource monitors (`DatResourceMonitor`), departmental cost showback (`HrDepartment` / `FinBudget`), and Steward-approved zero-copy outbound/inbound data shares (`DatDataShare`).

### Out-of-Scope
1. External SaaS/RDBMS extraction connectors, log-based CDC readers, and scheduled ELT pipeline orchestration — owned by `#098 Data Integration / ETL` (`data-integration`).
2. Executive drag-and-drop dashboard canvases, KPI scorecards, and scheduled PDF report bursting — owned by `#096 Business Intelligence & Dashboards` (`bi-dashboards`).
3. Enterprise business glossary stewardship, PII discovery scanning, and master access policy authoring — owned by `#100 Data Governance & Catalog` (`data-governance`).
4. Multi-language Python/R data science notebook execution cells — provided by Rapider Platform Notebooks (connected via `DWH-012` pushdown bridge).

### Cross-Suite Ownership & Integration Contract

| Domain / App | Owns (Single Source of Truth) | Integration Contract with `data-warehouse` (`#099`) |
| :--- | :--- | :--- |
| **`data-warehouse` (`#099`)** | `DatDatabaseCatalog`, `DatWarehouseTable`, `DatComputeCluster`, `DatSavedSqlWorksheet`, `DatQueryExecution`, `DatResourceMonitor`, `DatDataShare` | Executes analytical SQL, manages physical/Iceberg table metadata & Time Travel, and enforces compute FinOps quotas. |
| **`#098` Data Integration (`data-integration`)** | `DatSyncPipeline`, `DatTransformationModel` | Lands staging tables and runs pushdown SQL `DatTransformationModel`s on dedicated `ETL_INGEST` `DatComputeCluster`s. |
| **`#096` BI Dashboards (`bi-dashboards`)** | `DatSemanticModel`, `DatDashboard` | Queries curated `MARTS` `DatWarehouseTable`s and `DYNAMIC_TABLE`s via `BI_REPORTING` clusters; subscribes to `dat.warehouse.table.refreshed.v1`. |
| **`#100` Data Governance (`data-governance`)** | `DatCatalogAsset`, `DatDataAccessPolicy`, `DatClassificationTag` | Synchronizes table/column schemas to `#100` catalog and enforces `#100` row-access and column-masking policies dynamically at SQL query execution time. |
| **`HR` (`HrDepartment`), `APM` (`ApmProject`), `FIN` (`FinBudget`)** | Canonical department, project, and budget entities | Read-only linkage on `DatComputeCluster` and `DatResourceMonitor` for `Decimal128` FinOps chargeback/showback attribution. |

---

## 3. Primary Web Pages & Sidebar Navigation Architecture (12 Pages)

Every visible sidebar section strictly contains **`>= 3` visible items (`displayOnMenu: true`)**, while detail views and drawers set `displayOnMenu: false`.

| # | Route | Page Title | Sidebar Section | Menu Visible | Key Components & UX |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | `warehouse-overview` | Warehouse & FinOps Cockpit | `Storage & SQL` | `true` (Order 1) | Active compute cluster pulse, storage footprint (Active vs. Time-Travel vs. Iceberg), credit burn vs. `DatResourceMonitor` quota, `#activeFilterTagsBar`. |
| 2 | `catalog-explorer` | Databases & Tables | `Storage & SQL` | `true` (Order 2) | Hierarchical `DatDatabaseCatalog` & `DatWarehouseTable` browser (`findSWR`), format pills (`COLUMNAR`, `ICEBERG`, `DYNAMIC_TABLE`, `SUITE_MIRROR`), clickable table name, icon+text `Edit`, icon-only `Delete`. |
| 3 | `sql-worksheets` | SQL Worksheet Studio | `Storage & SQL` | `true` (Order 3) | Multi-tab `DatSavedSqlWorksheet` IDE, cluster selector, dry-run byte/cost badge, result grid + quick chart toggle, grounded SQL Copilot thread (`projectChannelMessage`). |
| 4 | `compute-clusters` | Compute Clusters | `Compute & Performance` | `true` (Order 4) | `DatComputeCluster` fleet table showing size (`XS`–`4XL`), state (`RUNNING`, `SUSPENDED`, `RESIZING`), `autoSuspendSeconds`, queue depth, and `Resume / Suspend` actions. |
| 5 | `query-history` | Query History & Live Queue | `Compute & Performance` | `true` (Order 5) | Searchable `DatQueryExecution` ledger with status/cluster filter pills, `#activeFilterTagsBar` + `Clear all`, bytes scanned, `Decimal128` credits, and `Cancel Running Query` action. |
| 6 | `dynamic-tables-clones` | Dynamic Tables & Clones | `Compute & Performance` | `true` (Order 6) | Declarative materialized/dynamic table lag monitor and Zero-Copy `DEV/QA` clone sandbox manager with expiration timers. |
| 7 | `resource-monitors` | FinOps Resource Monitors | `FinOps & Sharing` | `true` (Order 7) | `DatResourceMonitor` quota cards & tables, departmental `HrDepartment` chargeback breakdown (`Decimal128`), and AI Idle-Cluster right-sizing recommendations. |
| 8 | `data-shares` | Secure Data Sharing | `FinOps & Sharing` | `true` (Order 8) | Outbound & inbound `DatDataShare` listings, clean-room `k-anonymity` aggregation rules, recipient workspace status, and Home `WorkItem` approval state. |
| 9 | `storage-lifecycle` | Time Travel & Storage Hygiene | `FinOps & Sharing` | `true` (Order 9) | Point-in-time table restore console (`AS OF`), partition/clustering compaction health, and cold-staging cleanup rules. |
| 10 | `table-detail` | Table Schema, Preview & Time Travel | *(Hidden)* | `false` | Column schema + `#100` PII mask tags (`#/table-detail?id=...`), sample masked row preview, partition stats, Time-Travel snapshot slider, and `Back to Catalog`. |
| 11 | `query-profile-detail` | Query Execution Plan Profiler | *(Hidden)* | `false` | Operator DAG flamegraph (`#/query-profile-detail?id=...`: Scan -> Filter -> Join -> Agg), pruning ratio, spill diagnostics, and AI optimization hints. |
| 12 | `cluster-monitor-drawer` | Cluster, Monitor & Share Drawer | *(Hidden)* | `false` | Sliding creation/edit drawer for `DatComputeCluster`, `DatResourceMonitor`, and `DatDataShare`; enforces `finally` button reset and `closePageDrawer()`. |

---

## 4. Canonical Data Models (`Dat*` — 7 Models)

All models omit `projectId`, use platform UUID `id` + optimistic `version`, enforce `Decimal128` for credits/costs, and use `00000000-xxxx-xxxx-xxxx-xxxxxxxxxxxx` seed UUIDs.

| Model Name | Key Fields & Types | Relationships & External Refs | Invariants & Lifecycle |
| :--- | :--- | :--- | :--- |
| **`DatDatabaseCatalog`** | `id: UUID`, `databaseName: string`, `schemaName: string`, `environment: enum(DEV, QA, PROD)`, `layerType: enum(RAW, STAGING, INTERMEDIATE, MARTS, SUITE_MIRROR)`, `timeTravelRetentionDays: int`, `clonedFromCatalogId: UUID?`, `ownerDepartmentId: UUID?`, `version: int` | `clonedFromCatalogId -> DatDatabaseCatalog.id`; `ownerDepartmentId -> HrDepartment.id`. | `(databaseName, schemaName)` unique per workspace; `timeTravelRetentionDays` bounded `0..90`. |
| **`DatWarehouseTable`** | `id: UUID`, `catalogId: UUID`, `tableName: string`, `tableFormat: enum(NATIVE_COLUMNAR, APACHE_ICEBERG, VIEW, DYNAMIC_TABLE, SUITE_SHORTCUT)`, `columnsJson: {name, sqlType, nullable, maskingPolicyId}[]`, `partitionKeys: string[]`, `clusterKeys: string[]`, `targetLagMinutes: int?`, `rowCount: int`, `compressedBytes: int`, `timeTravelBytes: int`, `externalVaultRef: string?`, `lastRefreshedAt: datetime`, `version: int` | `catalogId -> DatDatabaseCatalog.id`; `maskingPolicyId -> DatDataAccessPolicy.id` (`#100`). | `(catalogId, tableName)` unique. `SUITE_SHORTCUT` tables are strictly read-only (`DML/DDL` mutations rejected). External Iceberg storage credentials must use `externalVaultRef` (zero plaintext keys). |
| **`DatComputeCluster`** | `id: UUID`, `code: string`, `name: string`, `workloadType: enum(ETL_INGEST, BI_REPORTING, ADHOC_ANALYST, DATA_SCIENCE)`, `sizeTier: enum(XS, S, M, L, XL, 2XL, 4XL)`, `minClusters: int`, `maxClusters: int`, `autoSuspendSeconds: int`, `autoResume: boolean`, `maxStatementTimeoutSeconds: int`, `maxBytesScannedPerQuery: int?`, `resourceMonitorId: UUID?`, `costCenterDepartmentId: UUID?`, `state: enum(RUNNING, SUSPENDED, RESIZING, SUSPENDED_BY_QUOTA)`, `version: int` | `resourceMonitorId -> DatResourceMonitor.id`; `costCenterDepartmentId -> HrDepartment.id`. | `1 <= minClusters <= maxClusters <= 10`; `autoSuspendSeconds >= 30`. When `state === 'SUSPENDED_BY_QUOTA'`, auto-resume is blocked until `DatResourceMonitor` quota is raised or reset. |
| **`DatSavedSqlWorksheet`** | `id: UUID`, `title: string`, `folderName: string`, `defaultCatalogId: UUID?`, `defaultClusterId: UUID?`, `sqlText: string`, `parametersSchemaJson: object[]`, `visibility: enum(PRIVATE, TEAM_SHARED)`, `discussionChannelId: UUID?`, `ownerUserId: UUID`, `version: int` | `defaultCatalogId -> DatDatabaseCatalog.id`; `defaultClusterId -> DatComputeCluster.id`; `discussionChannelId -> projectChannelMessage`. | Versioned on every save so analysts can diff/revert worksheet edits safely. |
| **`DatQueryExecution`** | `id: UUID`, `computeClusterId: UUID`, `worksheetId: UUID?`, `callerAppKey: string`, `executedByUserId: UUID`, `sqlFingerprint: string`, `sqlPreviewRedacted: string`, `status: enum(QUEUED, RUNNING, SUCCEEDED, CACHED_HIT, FAILED, ABORTED_TIMEOUT, ABORTED_SCAN_CAP, BLOCKED_QUOTA, CANCELED)`, `startedAt: datetime`, `completedAt: datetime?`, `durationMs: int`, `bytesScanned: int`, `bytesSpilled: int`, `creditsConsumed: Decimal128`, `planSummaryJson: object`, `idempotencyKey: string` | `computeClusterId -> DatComputeCluster.id`; `worksheetId -> DatSavedSqlWorksheet.id`. | Append-only audit log once terminal. Literal string parameters in `sqlPreviewRedacted` are scrubbed to avoid logging PII values in query history. |
| **`DatResourceMonitor`** | `id: UUID`, `name: string`, `scopeType: enum(WORKSPACE, COMPUTE_CLUSTER)`, `periodUnit: enum(DAILY, MONTHLY)`, `creditQuota: Decimal128`, `creditsUsed: Decimal128`, `unitPriceUsd: Decimal128`, `notifyAtPct: int`, `escalateWorkItemAtPct: int`, `suspendAction: enum(NONE, SUSPEND_AFTER_RUNNING, HARD_SUSPEND_AT_100)`, `linkedBudgetId: UUID?`, `activeWorkItemId: UUID?`, `version: int` | `linkedBudgetId -> FinBudget.id` (`FIN`); `activeWorkItemId -> Platform WorkItem.id`. | All credit and monetary fields use `Decimal128`. Crossing `escalateWorkItemAtPct` creates a FinOps Home `WorkItem`; reaching `100%` transitions bound clusters to `SUSPENDED_BY_QUOTA`. |
| **`DatDataShare`** | `id: UUID`, `shareCode: string`, `name: string`, `direction: enum(OUTBOUND, INBOUND)`, `sharedTableIds: UUID[]`, `recipientWorkspaceOrOrg: string`, `cleanRoomMinGroupSize: int?`, `expiresAt: datetime?`, `approvalStatus: enum(DRAFT, PENDING_STEWARD, ACTIVE, REVOKED, EXPIRED)`, `approvedByUserId: UUID?`, `activeWorkItemId: UUID?`, `version: int` | `sharedTableIds -> DatWarehouseTable.id[]`; `activeWorkItemId -> Platform WorkItem.id`. | Outbound shares cannot transition to `ACTIVE` without `Data Steward` approval via guarded command and must exclude tables containing unmasked PII tags unless `cleanRoomMinGroupSize >= 25`. |

---

## 5. Core End-to-End User Journeys (5 Journeys)

1. **Journey 1 — Dry-Run Cost Check, SQL Worksheet Execution & Promote to `#096` Semantic Model:**
   - An Analytics Engineer opens `sql-worksheets`, selects `ADHOC_ANALYST (XS)` cluster, and authors a cross-suite join across `SUITE_MIRROR.crm_opportunities` and `MARTS.fin_invoices`.
   - The live Dry-Run Estimator displays `14.2 MB scanned (~0.002 credits)` (`DWH-013`). Running the query records a `DatQueryExecution`, renders results + inline revenue bar chart, and clicking `"Promote to BI Semantic Model"` hands the governed view directly to `#096` (`bi-dashboards`).
2. **Journey 2 — FinOps Runaway Scan Block & Resource Monitor Quota Escalation via Home `WorkItem`:**
   - A junior user accidentally submits an unpartitioned cross-join estimated at `4.8 TB` on `ADHOC_ANALYST` (`maxBytesScannedPerQuery = 50 GB`). The engine deterministically rejects execution (`ABORTED_SCAN_CAP`) before burning credits (`DWH-020`).
   - Later in the month, `ETL_INGEST` reaches `92%` of its `DatResourceMonitor` `creditQuota`. The monitor workflow opens a Rapider Home `WorkItem` for the FinOps/Warehouse Admin (`DWH-019`) with a direct link to `resource-monitors` and AI right-sizing suggestions (`DWH-028`).
3. **Journey 3 — Zero-Copy Dev Sandbox Clone & Accidental Table Drop Time-Travel Recovery:**
   - Before refactoring `MARTS.customer_ltv`, an engineer runs `"Create Zero-Copy Clone"` on `dynamic-tables-clones`, creating `DEV_SANDBOX.customer_ltv` in `< 2 seconds` with `0` extra storage bytes (`DWH-005`).
   - When an authorized script mistakenly truncates a staging table, the Warehouse Admin opens `storage-lifecycle`, selects an `AS OF` timestamp 15 minutes prior (`DWH-004`), confirms the guarded restore modal (`#rapiderConfirmOkBtn`), and restores all rows intact.
4. **Journey 4 — Outbound Clean-Room Data Share Approval:**
   - A Partner Ops Lead configures an `OUTBOUND` `DatDataShare` (`cleanRoomMinGroupSize: 25`) on `data-shares` via `cluster-monitor-drawer` and submits for publication.
   - Status moves to `PENDING_STEWARD` and creates a Home `WorkItem`. The Data Steward inspects `#100` PII classifications on `table-detail`, approves the share (`ACTIVE`), and revokes access in one click once the partnership ends.
5. **Journey 5 — Query Bottleneck Profiling & State-Preserving Back Navigation:**
   - On `query-history`, an engineer filters by `Status: "SUCCEEDED"` and `Cluster: "BI_REPORTING"` (`#activeFilterTagsBar` renders both dismissible chips + `[Clear all]`), sorts by `durationMs DESC`, and clicks query ID `QRY-99412` to open `#/query-profile-detail?id=...`.
   - The flamegraph highlights `1.2 GB` disk spillage on an unclustered join key; clicking `"Back to Query History"` restores `query-history` with both active filter chips intact.

---

## 6. Consolidated Feature Priorities & Work Packages (`P0`, `P1`, `P2`)

### `P0` Foundation Work Packages
- **`WP-P0-1` Catalogs, Columnar/Iceberg Tables, Suite Mirrors & Time Travel (`DWH-001`, `DWH-002`, `DWH-003`, `DWH-004`):** Build `catalog-explorer`, `table-detail`, and `storage-lifecycle` supporting `Decimal128` columns, Iceberg tables, read-only canonical Rapider suite mirrors, and point-in-time Time Travel (`Data Engineer` / `Warehouse Admin`).
- **`WP-P0-2` Elastic Compute Pools & Auto-Suspend (`DWH-008`, `DWH-009`):** Build `compute-clusters` and `cluster-monitor-drawer` with workload isolation, instant auto-suspend/auto-resume, and statement timeouts (`Warehouse Admin`).
- **`WP-P0-3` SQL Worksheet Studio & Query Audit Ledger (`DWH-013`, `DWH-014`):** Build `warehouse-overview`, `sql-worksheets`, and `query-history` with schema autocomplete, dry-run byte estimation, and redacted query execution logs (`Analyst` / `Analytics Engineer`).
- **`WP-P0-4` FinOps Resource Monitors, Byte-Scan Caps & SQL RBAC (`DWH-019`, `DWH-020`, `DWH-021`):** Build `resource-monitors` enforcing `Decimal128` credit quotas, `maxBytesScannedPerQuery`, and `#100` dynamic row/column masking (`Warehouse Admin` / `FinOps`).

### `P1` Scale & Enterprise Governance Work Packages
- **`WP-P1-1` Zero-Copy Clones, Dynamic Tables & Compaction (`DWH-005`, `DWH-006`, `DWH-007`, `DWH-025`, `DWH-026`):** Build `dynamic-tables-clones`, automated Iceberg/partition compaction, cold staging archival, and Kafka DDL refresh events (`Data Engineer`).
- **`WP-P1-2` Multi-Cluster Autoscaling, Result Cache, Plan Profiler & Kill-Switch (`DWH-010`, `DWH-011`, `DWH-015`, `DWH-016`, `DWH-024`):** Build `query-profile-detail` flamegraphs, deterministic `< 100ms` result caching, live query cancellation, and one-click promotion to `#096`/`#098` (`Warehouse Admin` / `Analytics Engineer`).
- **`WP-P1-3` FinOps Departmental Showback & Secure Data Shares (`DWH-022`, `DWH-023`):** Build `data-shares` with Steward `WorkItem` approval and `HrDepartment`/`FinBudget` cost attribution (`FinOps` / `Data Steward`).

### `P2` Adjacent & Grounded AI Work Packages
- **`WP-P2-1` Grounded SQL Copilot, Partition Advisor & FinOps Right-Sizer (`DWH-017`, `DWH-018`, `DWH-028`):** Schema-grounded NL-to-SQL with destructive-DDL human confirmation gate, clustering advisor, and idle-cluster FinOps digests (`All SQL Users` / `FinOps`).
- **`WP-P2-2` Notebook Pushdown Bridge & Clean-Room Aggregation Shares (`DWH-012`, `DWH-027`):** Rapider Notebook pushdown connector and `k-anonymity` clean-room `DatDataShare` policies (`Data Scientist` / `Data Steward`).

---

## 7. Roles, Permissions & Field-Level Governance

| Role | Permitted Actions | Restricted / Field-Level Boundaries |
| :--- | :--- | :--- |
| **`Warehouse Reader / BI Consumer`** | Execute `SELECT` queries via `#096` or read-only `sql-worksheets` on granted `MARTS` schemas. | Dynamically masked per `#100` `DatDataAccessPolicy`; cannot run DDL/DML, resize clusters, or view other users' query text. |
| **`Data Analyst`** | Author/save `DatSavedSqlWorksheet`s, run dry-run cost estimates, create temporary views in personal sandbox schemas. | Bound by `maxBytesScannedPerQuery` and `#100` PII masking; cannot alter `PROD` tables or `DatResourceMonitor` quotas. |
| **`Data / Analytics Engineer`** | Create/alter `DatWarehouseTable`s and `DYNAMIC_TABLE`s in `RAW/STAGING/MARTS`, create zero-copy `DEV/QA` clones, inspect `query-profile-detail`. | Destructive `DROP`/`TRUNCATE` on `PROD` catalogs requires explicit confirmation + `MODIFY_PROD_CATALOG` grant; cannot self-approve outbound `DatDataShare`s. |
| **`FinOps Controller`** | Configure `DatResourceMonitor` `Decimal128` quotas, map `DatComputeCluster`s to `HrDepartment` and `FinBudget`, review idle-cluster advisors. | Cannot `SELECT` row contents of restricted business tables. |
| **`Warehouse & Security Admin`** | Provision/resize/suspend `DatComputeCluster`s, abort runaway queries, execute Time-Travel table restores, approve/revoke `DatDataShare`s (with Steward). | Zero ability to disable immutable `DatQueryExecution` audit logging. |

---

## 8. Technical APIs, Guarded Commands, Events & `requiredWorkflows`

### Guarded Commands
1. `dat.warehouse.executeSqlStatement({ clusterId, catalogId, sqlText, bindParams, dryRunOnly, idempotencyKey, correlationId })` — Enforces RBAC + `#100` row/column policies, checks `DatResourceMonitor` state and `maxBytesScannedPerQuery`, and records `DatQueryExecution`.
2. `dat.warehouse.manageComputeCluster({ clusterId, action: 'CREATE' | 'RESIZE' | 'SUSPEND' | 'RESUME', spec, expectedVersion, idempotencyKey, correlationId })` — Transitions elastic cluster state safely.
3. `dat.warehouse.cloneCatalogOrTable({ sourceId, targetName, expirationDays, idempotencyKey, correlationId })` — Creates metadata-only zero-copy clone referencing immutable parent storage snapshots.
4. `dat.warehouse.restoreTableTimeTravel({ tableId, asOfTimestamp, confirmationToken, expectedVersion, idempotencyKey, correlationId })` — Restores `DatWarehouseTable` snapshot after mandatory human confirmation.
5. `dat.warehouse.governDataShare({ shareId, decision: 'SUBMIT' | 'APPROVE' | 'REVOKE', expectedVersion, idempotencyKey, correlationId })` — Manages `DatDataShare` lifecycle and Steward Home `WorkItem`s.

### Domain Events Published & Consumed (Kafka)
- **Published:** `dat.warehouse.table.refreshed.v1`, `dat.warehouse.schema.altered.v1`, `dat.warehouse.cluster.suspended_by_quota.v1`, `dat.warehouse.resource_monitor.threshold_crossed.v1`, `dat.warehouse.data_share.activated.v1`.
- **Consumed:** `dat.etl.sync_run.succeeded.v1` (from `#098` to refresh `DYNAMIC_TABLE` metadata), `dat.governance.access_policy.updated.v1` (from `#100` to invalidate cached SQL results affected by policy changes).

### `requiredWorkflows`
- `warehouseAutoSuspendMonitorWorkflow` — Suspends idle compute clusters once `autoSuspendSeconds` elapses with zero active queries.
- `warehouseResourceMonitorEnforcementWorkflow` — Evaluates `Decimal128` credit burn, creates `90%` FinOps Home `WorkItem`s, and suspends clusters at `100%`.
- `warehouseDynamicTableRefreshWorkflow` — Maintains declarative `targetLagMinutes` freshness on `DYNAMIC_TABLE`s.
- `warehouseDataShareApprovalWorkflow` — Orchestrates Steward Home `WorkItem` verification before activating outbound shares.

### Grounded Rapider AI Governance Rules
- SQL Copilot (`DWH-017`) is strictly grounded in schemas where the caller holds `USAGE`/`SELECT` permissions, never sees raw table rows unless explicitly sampled under `#100` masking rules, and **MUST NEVER** execute `DROP`, `TRUNCATE`, `DELETE`, `ALTER`, or `GRANT` statements without explicit user confirmation in UI.

---

## 9. Security, Privacy, Compliance & Non-Functional Requirements

- **Accidental Data-Loss Prevention & Encryption:** Destructive DDL (`DROP TABLE/SCHEMA`, `TRUNCATE`) requires explicit typed confirmation in a custom modal (`#rapiderConfirmOkBtn`) and retains recoverable micro-partitions for `timeTravelRetentionDays` (default 14 days in `PROD`). All storage micro-partitions, Iceberg Parquet files, and cached result sets are encrypted at rest (AES-256) and in transit (TLS 1.3).
- **Dynamic Policy Enforcement & Redacted Logs:** SQL queries automatically rewrite through `#100` row-access/column-masking policies; literal query bind parameters are scrubbed in `DatQueryExecution.sqlPreviewRedacted` for GDPR/HIPAA/SOC 2 compliance.
- **Exact Financial Precision:** Credit consumption (`creditsConsumed`), monthly FinOps budgets (e.g., `\$15,000.00` compute cap), and `DECIMAL(38,10)` columns preserve `Decimal128` accuracy; zero `projectId` fields or plaintext cloud storage keys exist in app schemas.
- **Accessibility & Responsive UX:** WCAG 2.2 AA accessible SQL editor shortcuts, screen-reader tabular fallbacks for query plan DAGs, `#ffffff !important` contrast on primary/danger buttons, and responsive layouts across `390px`, `768px`, and `1440px`.

---

## 10. Deterministic Acceptance Criteria (14 Testable Criteria)

1. **AC-01 (Sidebar Minimum-3 Rule):** Visible sidebar sections (`Storage & SQL`: 3 items, `Compute & Performance`: 3 items, `FinOps & Sharing`: 3 items) each contain `>= 3` `displayOnMenu: true` pages; `table-detail`, `query-profile-detail`, and `cluster-monitor-drawer` set `displayOnMenu: false`.
2. **AC-02 (SWR Clean Queries & Defensive Soft-Delete):** All 9 sidebar routes load initial state via `findSWR`/`countSWR` with zero `isDeleted` client query predicates and apply defensive `item.isDeleted !== true` in-memory filtering.
3. **AC-03 (Table Actions & Click-Through Navigation):** Zero `"View"` buttons exist in `Actions` columns; clicking a table name on `catalog-explorer` navigates to `#/table-detail?id=...` and clicking a query ID on `query-history` navigates to `#/query-profile-detail?id=...` without `<base href>` 404 diversion; `Edit` renders icon+text and `Delete` renders an icon-only button.
4. **AC-04 (Active Filter Tags & Clear All):** Filtering `query-history` or `catalog-explorer` by status, cluster, or format renders `#activeFilterTagsBar` with HTML-escaped dismissible chips and `[Clear all]`, synchronously updating rows and counts.
5. **AC-05 (Drawer Lifecycle & Optimistic State):** Creating/resizing a `DatComputeCluster` or editing a `DatResourceMonitor` in `cluster-monitor-drawer` resets button state in `finally`, clears SWR caches, updates parent lists optimistically, and closes the drawer via `closePageDrawer()`.
6. **AC-06 (Read-Only Suite Mirror Invariant):** Executing `INSERT`, `UPDATE`, `DELETE`, or `DROP` against a `SUITE_SHORTCUT` `DatWarehouseTable` in `sql-worksheets` is deterministically rejected with `403 Read-Only Canonical Mirror`.
7. **AC-07 (Per-Query Byte-Scan Cap Enforcement):** Submitting a query whose dry-run scan estimate exceeds `DatComputeCluster.maxBytesScannedPerQuery` aborts execution immediately with status `ABORTED_SCAN_CAP` and `0.00` `creditsConsumed`.
8. **AC-08 (`Decimal128` Resource Monitor Auto-Suspend & `WorkItem`):** When cumulative `Decimal128` `creditsUsed` crosses `escalateWorkItemAtPct` (`90%`), a FinOps Home `WorkItem` is created; at `100%` with `HARD_SUSPEND_AT_100`, bound clusters transition to `SUSPENDED_BY_QUOTA` and block new queries.
9. **AC-09 (Policy-Scoped Result Cache Isolation):** Two users with different `#100` row/column masking policies running the exact same SQL text on `sql-worksheets` never share an unmasked `CACHED_HIT` result set.
10. **AC-10 (Zero-Copy Clone & Time-Travel Restore):** Cloning a table creates a `DatWarehouseTable` with `0` initial additional storage bytes, and invoking `dat.warehouse.restoreTableTimeTravel` restores prior row counts accurately after modal confirmation.
11. **AC-11 (Outbound Data Share Steward Gate):** Attempting to activate an `OUTBOUND` `DatDataShare` without `Data Steward` approval fails with `403`, and tables with unmasked PII are blocked unless `cleanRoomMinGroupSize >= 25`.
12. **AC-12 (Destructive DDL Confirmation & Zero Native Dialogs):** Running `DROP` or `TRUNCATE` in `sql-worksheets` pauses for explicit confirmation via custom Rapider modal (`#rapiderConfirmOkBtn`) with zero `window.confirm`/`alert` calls.
13. **AC-13 (Back Navigation Filter Preservation):** Navigating from `query-history` (filtered by `Cluster: "BI_REPORTING"`) to `query-profile-detail` and clicking `#btnGoBack` restores `query-history` with `Cluster: "BI_REPORTING"` intact.
14. **AC-14 (Theme & Contrast Compliance):** All 12 routes pass light/dark `validate_theme` checks with `#ffffff !important` white text on primary/danger buttons.
