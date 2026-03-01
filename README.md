# FOIA Public Records Tool (ELC)

## Overview

The **FOIA Public Records Tool** is an internal web application developed for **Environmental Logistics & Consulting (ELC)** to streamline the preparation and submission of public records (FOIA) requests during Phase I Environmental Site Assessments.

The tool centralizes jurisdictional contact data and dynamically generates department-specific FOIA request language based on a property’s city and county. This reduces manual lookup time, improves consistency, and minimizes jurisdictional errors when requesting records from local agencies.

The application is built with **Python** and **Streamlit** and is intended for internal operational use.

---

## Core Capabilities

### Jurisdiction-Based Contact Resolution

* Determines the appropriate city/municipality and county for a given property address
* Matches the jurisdiction against a maintained master contact directory
* Handles incorporated, unincorporated, and county-level jurisdictions

### Department-Specific FOIA Templates

* Building
* Planning / Zoning
* Fire
* Environmental / Health
* All-in-one (multi-department) request

Templates are pre-aligned with ASTM E1527 Phase I ESA record-search requirements and automatically populated with project details.

### Contact Directory

* Centralized Excel-based data source (`master.xlsx`)
* Supports multiple department types per jurisdiction
* Stores emails, portals, preferred submission methods, and verification metadata

### Automated Email Assembly

* Auto-generates subject lines and email bodies per department
* Displays resolved recipient email lists
* Supports copy-paste ready FOIA request packages

### Miami-Dade APN Validation

* Uses folio (APN) prefixes to validate municipality selection
* Warns when an entered city does not align with the expected jurisdiction

### External Records Integration

* Quick access to Florida DEP OCULUS search
* Embedded browser view for convenience

---

## Application Structure

```
foia/
├── app.py              # Main Streamlit application
├── requirements.txt    # Python dependencies
├── data/
│   └── master.xlsx     # Jurisdiction & contact directory
├── venv/               # Local virtual environment 
└── README.md
```

---

## Technology Stack

* **Python 3.11+**
* **Streamlit** (UI framework)
* **Pandas** (data processing)
* **Requests** (external API calls)
* **OpenPyXL** (Excel ingestion)
* **python-docx** (document handling support)

---

## Data Management

The contact directory is maintained in:

```
data/master.xlsx
```

Required columns include:

* County
* City / Municipality
* Dept Type
* Dept Name

Optional metadata fields:

* Contact name
* Email(s)
* Phone
* Portal URL
* Preferred submission method
* Verification status and date

The application performs normalization on county and city names to improve match reliability.

---

## Intended Use

This tool is designed to:

* Support Phase I ESA records research
* Improve efficiency and consistency in FOIA submissions
* Reduce jurisdictional lookup errors

It is **not** intended for public deployment or external client access.

---

## Maintenance Notes

* Jurisdiction accuracy depends on the quality of `master.xlsx`
* New municipalities or departments should be added to the data file, not hard-coded
* FOIA language templates can be updated in `app.py` under the template definitions

---

## Internal Status

* Actively used by ELC
* Local-first execution
* Version-controlled via GitHub

---

## License

Internal use only. Distribution outside of ELC requires authorization.
