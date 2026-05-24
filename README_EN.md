🦴 INTO – Hip Surgery Material Selection System
A web application for selecting and managing surgical materials for hip surgeries at the Instituto Nacional de Traumatologia e Ortopedia Jamil Haddad (INTO) — Brazil's National Institute of Traumatology and Orthopedics. Built specifically to help surgical residents quickly identify the correct instrument boxes and materials for each procedure.


✨ Features
Module
Description
📊 Dashboard
Real-time statistics and quick access by surgery type
📦 Surgical Boxes
Full catalog with filters by surgery type, manufacturer, and free text search
🩺 Diagnoses
Clinical diagnoses linked to recommended boxes and materials
🔩 Materials
Catalog of implants, instruments, disposables, and equipment
📄 Documents
Protocols and technical sheets with links to Google Drive files
👤 Patients
Surgical records with phase tracking (pre/post-operative)
🔬 Imaging Exams
X-rays, CT scans, and MRIs linked to patient records



🎯 For Residents
The intended workflow is straightforward:

Go to Surgical Boxes
Filter by surgery type (e.g. Total Hip Arthroplasty, Revision, Arthroscopy…)
Optionally filter by manufacturer (Zimmer Biomet, Smith & Nephew, DMO…)
Use free text search to find specific instruments
Click a box to see its full instrument list and extracted document content


🏗️ Architecture
This is a single-page application built with plain HTML, CSS, and vanilla JavaScript — no framework dependencies. All data persistence is handled via the Base44 REST API.

quadril_into_app.html   ←  Complete app (HTML + CSS + JS in a single file)
API
Field
Value
Base URL
https://ortho-link-flow.base44.app/api
App ID
69dd6b3d791b89ea670983cf
Auth
api_key request header

API Entities
Entity
Purpose
SurgicalBox
Instrument boxes / trays
SurgicalMaterial
Individual materials and instruments
Diagnosis
Clinical diagnoses
Patient
Patient surgical records
ImagingExam
Pre/post-operative imaging
DescriptiveDocument
Protocols and technical documents



🚀 Running Locally
No installation required. Just download the file and open it in any browser:

# Clone the repository

git clone https://github.com/YOUR_USERNAME/into-quadril-app.git

# Open the app

open into-quadril-app/quadril_into_app.html

Or access it via GitHub Pages (if configured):

https://YOUR_USERNAME.github.io/into-quadril-app


📦 Supported Surgery Types
Code
Description
artroplastia_total
Total Hip Arthroplasty (THA)
artroplastia_parcial
Partial Hip Arthroplasty (Hemiarthroplasty)
revisao
Revision Surgery
artroscopia
Hip Arthroscopy
osteossintese
Osteosynthesis / Fracture Fixation
geral
General Procedures



🏭 Manufacturers Covered
Zimmer Biomet — Avenir, G7, CPT, ML Taper, Wagner SL, Trilogy IT, Dual Mobility
Smith & Nephew — Polarstem, R3, Mini Acetabulum
DMO — Plasmafit, Metha
Medacta / Osseus — Amistem, AMIS, Versafit
WM — Wagner SL, NCB, ZMR
Arthrex — Hip Arthroscopy systems


🔧 Contributing
Fork this repository
Create your feature branch: git checkout -b feature/my-improvement
Commit your changes: git commit -m 'Add filter by component size'
Push to the branch: git push origin feature/my-improvement
Open a Pull Request
Suggested improvements
Bulk import of 133 Word documents from Google Drive
Photos of instrument boxes and trays
Interactive surgical checklist per procedure
Offline mode / PWA support
Sterilization tracking with expiry date alerts
Native mobile app version
Multi-language support (PT/EN)


🗂️ Data Model Overview
SurgicalBox

 ├── name, code, surgical_type, status

 ├── extracted_content   (full text from Word document)

 ├── extracted_items[]   (individual instrument list)

 └── document_file_url   (link to original Google Drive file)

SurgicalMaterial

 ├── name, code, category, manufacturer

 ├── surgical_type, status, quantity, unit

 └── document_id → DescriptiveDocument

Diagnosis

 ├── name, code (ICD-10), surgical_type

 ├── recommended_box_ids[]

 └── recommended_material_ids[]

Patient

 ├── full_name, record_number, birth_date, gender

 ├── surgical_type, surgery_date, surgeon, status

 └── box_ids[]


🏥 Clinical Context
This system was built for the Hip Surgery Group at INTO, with the goals of:

Reducing material selection errors by inexperienced residents
Centralizing information about 133+ catalogued instrument boxes
Streamlining pre-operative planning
Tracking surgical patients through their care journey

The instrument data comes from a catalog of ~133 Word documents stored on Google Drive, each describing the contents of one surgical box (instruments, implants, sterilization method, packaging type, and missing items).


📄 License
alceufjr/into-quadril-app is licensed under the Apache License 2.0
A permissive license whose main conditions require preservation of copyright and license notices. Contributors provide an express grant of patent rights. Licensed works, modifications, and larger works may be distributed under different terms and without source code.
