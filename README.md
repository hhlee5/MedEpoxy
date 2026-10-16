# MedEpoxy
**Synthetic data only. Do not enter real patient information.**

## Live Demo
https://hhlee5.github.io/MedEpoxy/

## Concept

- AI-powered treatment coordination between care team members in the clinic, with humans in the loop.
- Drafts admin tasks, such as extracting information from physician notes to fill out the prior authorization (PA). A nurse, coordinator, or other team member confirms its accuracy before anything is used.
- Treatment coordination is overwhelming and fragmented. MedEpoxy divides the tasks among the care team, so no single person runs the whole process.
- Offloads the cognitive load of keeping track and working out next steps in complicated cases.
- Learns from each clinic. It refines the extra steps it suggests and who they are assigned to, so it can be tailored to that clinic's team and workflow.

## Where AI fits

| Area | In this prototype | Planned |
|---|---|---|
| Reading denial letters and issue notes, then suggesting next steps and who does them | Claude, when run as a Claude artifact. Falls back to keyword rules elsewhere. | Grounded in each payer's published criteria |
| Extracting PA fields from the clinic note | Rule-based. A person confirms each value. | Model-based, for messier free-text notes |
| Splitting work by role and writing handoff notes | Fixed templates | Tailored to the patient and clinic |
| Refining suggested steps and assignments per clinic | Not built | Learns from what each team edits, removes, adds, and reassigns |

Every suggestion is a draft. A person approves it before anything is added or assigned.

## How it works

The prototype has three tabs:

### Review note

Reads a clinic note, pulls out what a Maryland Medicaid PA needs, flags what is missing, and prefills the state form (MDH 070121). A person approves before anything is created.

### Plan

One patient's whole treatment episode, from prior authorization to cure, shared by the care team.

- **Patient banner:** Pick a patient at the top. The banner shows name, age, sex, MRN, payer, episode day, and any access barriers.
- **Status strip:** Names the next step, or the step that is running late, and who owns it.
- **Progress rail:** One dot per step shows what is done, next, waiting, or stalled.
- **Task table:** Every step is listed with its status, owner, and due day. Nothing is hidden or merged.

Each step has these actions:

- **Done:** Marks the step complete and records who did it and when. The step waiting on it becomes Next.
- **Issue:** Opens a box to type what happened, or paste or upload a letter. The tool suggests next steps. Each can be edited, removed, or added to. Only approved steps are added. They appear right after the step that caused them, tagged "Added after ... issue".
- **Undo:** Reverses a step and asks why. The reason is logged. Any steps the issue added are removed with it.
- **Expand:** Shows the instructions, what the step is waiting on, the note, the outcome, what was reported, and what it led to. Done steps have an Add/Edit note button.

How the team uses it:

- Each step belongs to one role: Care coordinator, Nurse, Physician, Medical assistant, or Social worker.
- A step stays Waiting until the one before it is done. The expanded view shows which step it waits on and who owns it.
- Marking a step done here or in My tasks updates both, because they share the same data.

Demo controls: **Skip ahead 3 days** makes steps run late. **Reset demo** restores every patient. **+ New task** adds a step of your own.

Sample patients:

- Complicated cases with denials or delays: James O., Rosa G., Angela W.
- Straightforward cases: Tomas P., Denise R., Luis M.
- New patient: Priya S.
- From the Review note: Marcus T.

### My tasks

Shows one role's steps across all patients, plus the steps held up by someone else. A Details link on a waiting step shows the task that is holding it up.

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
