# Market Opportunity Analysis Plan: Antibiotics for Prosthetic Joint Infections

## Objective
Create a comprehensive, presentation-ready Jupyter notebook analyzing market opportunities for Rifampicin-based antibiotics targeting prosthetic joint infections (hip and knee) in Germany.

---

## Key Parameters

| Parameter | Value | Source |
|-----------|-------|--------|
| **Infection rate** | 1-2% | Briefing document (conservative) |
| **Primary analysis** | OPS procedure codes | 5-820 to 5-823 |
| **Secondary analysis** | ICD-10 surrogate | M16.0/M16.1, M17.0/M17.1 (with exclusions) |
| **Target antibiotic** | Rifampicin | Client specification |
| **Target departments** | Chirurgie, Orthopädie | Expert input |
| **Hospital type focus** | Vollversorger | Largest hospital category |
| **Time range** | 2018-2023 | Multi-year validation |

---

## Note on DRG Data Availability

**DRG codes I44A-C (knee) and I47A-C (hip) are the gold standard per the briefing, but are NOT available in GBA quality reports.**

The German DRG system is managed by [InEK](https://mtrconsult.com/news/2026-drg-catalog-released-germany). Key findings:
- **Hospital-level DRG data is not publicly available** - only aggregated cost weights
- **GBA quality reports contain OPS and ICD-10** but not DRG assignments
- **Potential data sources for DRG:** InEK portal, AOK/Barmer claims data, Destatis

**Recommendation:** OPS codes 5-820 to 5-823 are the best available proxy.

---

## Note on Age Distribution (Backlog)

**Destatis provides national age distribution for ICD-10 and OPS codes:**
- Source: [Destatis Genesis - Statistic 23141](https://www-genesis.destatis.de/datenbank/online/statistic/23141/details/search/s/RFJH)
- **Caveat:** Data is aggregated across all of Germany (not hospital-level)
- **Use case:** Could validate age distribution assumptions (≥50/55 filter from briefing)
- **Status:** Backlog task for future enrichment

---

## Critical Caveat: OAU (Observed Antibiotic Use)

**The OAU metric is highly directional and should be treated with caution.**

- **No actual Rifampicin usage data exists** in GBA quality reports
- **No DDD (Defined Daily Doses)** or therapy days available
- **Proxy approach:** Text-based keyword search in hospital service offerings
- **This can only indicate awareness/capability, not actual consumption**

The AAI derived from this proxy is **indicative only**.

---

## Notebook Structure (Presentation-Ready)

**Flow: 2023 baseline first → Multi-year trend validation → TAM → Hospital/Regional breakdown**

### Section 1: Executive Summary
*→ PPT Slide: Key Findings at a Glance*
- Total market size (primary implants)
- Expected infection cases (1-2% range)
- Market trend (stable/growing)
- Top target hospitals
- Key regional insights

### Section 2: Business Context
*→ PPT Slide: Why Rifampicin for PJI?*
- Periprosthetic joint infection background
- Biofilm challenge
- Rifampicin opportunity

### Section 3: Methodology Overview
*→ PPT Slide: Our Approach*
- Data source: GBA quality reports
- Primary metric: OPS procedure codes (5-820 to 5-823)
- Secondary validation: ICD-10 surrogate
- ICD surrogate should be restricted to stationary cases and main diagnosis *if available in GBA data*; otherwise call out as a limitation
- Proxy limitations explained

### Section 4: OPS Procedure Analysis (PRIMARY) - 2023 Baseline
*→ PPT Slides: Market Size by Procedure Type*
- **Focus on most recent year (2023) as baseline**
- Hip primary (5-820): ~262k procedures
- Hip revision (5-821): ~20k procedures
- Knee primary (5-822): ~222k procedures
- Knee revision (5-823): ~15k procedures
- **Total primary implants: ~485k**
- Hospital count performing procedures

### Section 5: Multi-Year Trend Analysis (Deep Dive)
*→ PPT Slide: Market Stability & Growth Opportunity*
- **Purpose:** Validate if 2023 baseline is representative or if there's a trend
- 2018-2023 procedure volumes for OPS 5-820 to 5-823 only
- Year-over-year trend chart
- COVID dip identification (2020-2021)
- **Key question:** Stable market or growth opportunity?
- Recommendation on using single year vs. multi-year average

### Section 6: ICD-10 Surrogate Analysis (SECONDARY)
*→ PPT Slide: Validation via Diagnosis Codes*
- Inclusion: M16.0, M16.1 (hip), M17.0, M17.1 (knee)
- **Exclusions per briefing:**
  - T84.* (prosthetic complications)
  - Z96.6 (existing joint prosthesis)
  - M00.* (septic arthritis)
- ICD-10 are diagnoses (not procedures); treat as surrogate only and note stationär/Hauptdiagnose filters if feasible
- Comparison: ICD surrogate vs OPS counts
- Correlation analysis to validate OPS approach

### Section 7: Total Addressable Market (TAM)
*→ PPT Slide: Market Sizing*
- Procedure volumes (from Section 4)
- **Expected Infection Index (EII):**
  - Conservative (1%): ~4,850 infections
  - Mid-range (1.5%): ~7,270 infections
  - Upper bound (2%): ~9,700 infections
- Estimated market value scenarios (if treatment cost assumptions available)

### Section 8: OAU Proxy Analysis
*→ PPT Slide: Antibiotic Awareness Indicator (with caveats)*
- Keyword search: rifamp*, biofilm, periprothetisch, antibiot*
- **Clear caveat:** Awareness/capability proxy only, not actual usage
- National distribution of proxy scores
- Scope note: client target is Rifampicin; highlight that other biofilm-relevant antibiotics/substitution may not be captured

### Section 9: Hospital Opportunity Ranking
*→ PPT Slides: Target Hospital Lists*
- **Hospital characteristics integrated here:**
  - Type classification (Vollversorger focus via IK prefix)
  - Department validation (Chirurgie/Orthopädie)
- Composite opportunity scoring:
  - Volume (40%)
  - Gap proxy (30%)
  - Departments (15%)
  - Hospital type (15%)
- **Tiered target lists:**
  - Tier 1: High volume + Vollversorger + relevant depts + low AAI
  - Tier 2: Medium volume + relevant depts + low AAI
  - Tier 3: Reference centers (high revision rate)
- If AAI is computed from proxy OAU, label as *directional* and include briefing thresholds (<0.7 under‑, 0.7–1.3 normal, >1.3 over/center effect)

### Section 10: Geographic Analysis
*→ PPT Slides: Regional Market View*
- Bundesland comparison (procedure volumes, hospital counts)
- Hospital map visualization
- Regional opportunity hotspots

### Section 11: Recommendations & Next Steps
*→ PPT Slide: Recommended Actions*
- Priority hospitals for field team
- Regional focus areas
- Suggested validation steps

### Section 12: Limitations & Data Gaps
*→ PPT Slide: What We Cannot Answer*

**Briefing requirements we CANNOT address with GBA data:**

| Briefing Requirement | Available? | Gap Description |
|---------------------|------------|-----------------|
| DRG codes I44/I47 (gold standard) | ❌ No | Used OPS as proxy |
| Patient age filter (≥50/55) | ❌ No | No demographics (see Destatis backlog) |
| Actual antibiotic consumption (DDD) | ❌ No | No pharmacy data |
| Rifampicin therapy days | ❌ No | No treatment duration |
| Outpatient follow-up treatment | ❌ No | Only inpatient data |
| Case-level infection linkage | ❌ No | Cannot link procedures to infections |
| Antibiotic Adequacy Index (true) | ❌ No | Only text proxy available |
| Hospital case mix adjustment | ⚠️ Partial | Revision rate as complexity proxy |
| Supply level (Versorgungsstufe) | ⚠️ Partial | IK prefix approximation |
| Stationary + main diagnosis filter for ICD | ⚠️ Unknown | Only if GBA fields allow; otherwise limitation |
| ICD-10 is diagnosis not procedure | ❌ No | Surrogate only; exposure measured via OPS |
| Antibiotic substitution effects | ❌ No | Other biofilm antibiotics may replace Rifampicin |

**Data sources that could fill gaps:**
- InEK DRG database (institutional access)
- AOK/Barmer claims data (payer partnerships)
- IQVIA/Insight Health pharmacy data (commercial)
- Destatis for age distribution
- Hospital surveys (primary research)

---

## Implementation Steps

### Step 1: Setup and Configuration
```python
OPS_HIP_PRIMARY = ['5-820']
OPS_HIP_REVISION = ['5-821']
OPS_KNEE_PRIMARY = ['5-822']
OPS_KNEE_REVISION = ['5-823']

ICD_SURROGATE = ['M16.0', 'M16.1', 'M17.0', 'M17.1']
ICD_EXCLUSIONS = ['T84', 'Z96.6', 'M00']

INFECTION_RATE_LOW = 0.01
INFECTION_RATE_HIGH = 0.02
```

### Step 2: OPS 2023 Baseline (Section 4)
National procedure counts for 2023 - establish baseline.

### Step 3: Multi-Year Trend Query (Section 5)
```sql
SELECT Berichtsjahr,
  SUM(CASE WHEN OPS_301_Category LIKE '5-820%' THEN Anzahl ELSE 0 END) AS hip_primary,
  SUM(CASE WHEN OPS_301_Category LIKE '5-821%' THEN Anzahl ELSE 0 END) AS hip_revision,
  SUM(CASE WHEN OPS_301_Category LIKE '5-822%' THEN Anzahl ELSE 0 END) AS knee_primary,
  SUM(CASE WHEN OPS_301_Category LIKE '5-823%' THEN Anzahl ELSE 0 END) AS knee_revision,
  COUNT(DISTINCT IK) AS hospital_count
FROM VIEW_Krankenhaus_Prozedur
WHERE Berichtsjahr BETWEEN 2018 AND 2023
  AND (OPS_301_Category LIKE '5-820%' OR OPS_301_Category LIKE '5-821%'
       OR OPS_301_Category LIKE '5-822%' OR OPS_301_Category LIKE '5-823%')
GROUP BY Berichtsjahr
ORDER BY Berichtsjahr
```

### Step 4: ICD Surrogate with Exclusions (Section 6)
Net exposure = surrogate (M16/M17) - exclusions (T84/Z96.6/M00).

### Step 5: TAM / EII Calculation (Section 7)
Apply 1-2% infection rate to primary implant totals.

### Step 6: OAU Proxy (Section 8)
Text-based keyword search, clearly labeled as directional.

### Step 7: Hospital-Level Breakdown (Section 9)
- Procedure counts per hospital
- Hospital type (IK prefix)
- Department validation (Chirurgie/Orthopädie)
- Opportunity scoring

### Step 8: Geographic Breakdown (Section 10)
- State-level aggregation
- Map visualization

### Step 9: Export Deliverables
- CSV: Full hospital ranking
- Excel: Tier 1/2/3 target lists
- Excel: Regional summary
- Excel: Multi-year trends

---

## Critical Files

| File | Purpose |
|------|---------|
| `antibioticum_market_opportunity.ipynb` | Main notebook to extend |
| `icd_search_2026.ipynb` | Reference for SQL patterns |
| `all_data.db` | SQLite database |
| `Briefing_DRG_ICD_Klinikranking.docx` | Business requirements |

---

## Verification Checklist

1. ✅ All cells run without errors
2. ✅ Section 4 establishes 2023 OPS baseline FIRST
3. ✅ Section 5 validates with multi-year trend (2018-2023) on relevant OPS codes only
4. ✅ Multi-year analysis answers: stable or growing market?
5. ✅ ICD analysis includes exclusions (T84, Z96.6, M00), clearly SECONDARY
6. ✅ TAM/Market sizing appears BEFORE hospital breakdown
7. ✅ Hospital characteristics folded into Section 9
8. ✅ OAU proxy has prominent caveats
9. ✅ EII uses 1-2% infection rate
10. ✅ Section 12 lists all unanswerable briefing requirements
11. ✅ Destatis age data noted as backlog option
12. ✅ Flow: 2023 baseline → Trend validation → TAM → Hospital → Regional
