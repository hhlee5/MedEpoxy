# MedEpoxy

**Synthetic data only. Do not enter real patient information.**

## Concept

- AI-powered treatment coordination between care team members in the clinic, with humans in the loop.
- Automates admin tasks, such as extracting information from physician notes to fill out the prior authorization (PA). A nurse, coordinator, or other team member confirms its accuracy before anything is used.
- Treatment coordination is overwhelming and fragmented. MedEpoxy divides the tasks among the care team, so no single person runs the whole process.
- Offloads the cognitive load of keeping track and working out next steps in complicated cases.

## What it does

- **Review note:** Reads a clinic note, pulls out what a Maryland Medicaid PA needs, flags what is missing, and prefills the state form (MDH 070121). A person approves before anything is created.
- **Plan:** Shows every step of a patient's treatment episode, who owns it, and what it is waiting on. Each step expands to show instructions, notes, outcomes, and any detours, such as a denial that adds new steps.
- **My tasks:** Shows one role's steps across all patients (Care coordinator, Nurse, Physician, Medical assistant, Social worker), plus the steps held up by someone else.
- **Issue handling:** When a step goes wrong, a team member pastes or uploads a letter or types a note. The tool suggests next steps. Each suggestion can be edited, removed, or added to, and nothing is added without a person's approval.

## Run it

Open `index.html` in a browser. Everything is in one file. It needs internet access for fonts and the PDF libraries (pdf-lib, pdf.js).

The console message "Setting up fake worker" comes from pdf.js and is harmless.

## What is real and what is simulated

- The sample patients, their histories, and the chart data are made up.
- The denial reading uses Claude when the page runs as a Claude artifact. In any other setting it falls back to simple keyword rules.
- The suggested next steps for each denial type are placeholders. They have not been checked against real Maryland denial letters.
- Maryland Medicaid criteria reflect the May 2026 public policy. Confirm them against the current policy before relying on them.
- The extraction check (145 of 145) uses synthetic notes. It is not a clinical validation.

## Sources

- Maryland Medicaid hepatitis C PA criteria and form MDH 070121 (Maryland Department of Health)
- Illinois Medicaid preferred drug list (no PA for preferred drugs since 7/1/2023)

## Status

Early prototype built for a Nucleate Activator application. Not a medical device. Not for clinical use.

## Contact

Hannah, MedEpoxy founder
