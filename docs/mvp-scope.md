# MVP Scope

## Purpose

This document defines the scope of the first minimum viable product for PC Diagnostic Assistant.

The MVP is not intended to represent the complete long-term vision of the application. Its purpose is to prove that the core diagnostic workflow can be implemented successfully and provide useful value to users.

The MVP should demonstrate that the application can:

* Collect diagnostic information from Windows.
* Convert technical data into evidence and findings.
* Organise findings within an investigation.
* Generate cautious hypotheses and recommendations.
* Preserve diagnostic progress.
* Present results clearly through a desktop interface.

The MVP should remain deliberately small enough to complete, test, and refine before more advanced diagnostic capabilities are introduced.

---

# MVP Goal

The first version should answer the following question:

> Can PC Diagnostic Assistant collect a small amount of useful system information, identify clear concerns, explain the supporting evidence, and organise the result into a saved diagnostic investigation?

The MVP does not need to diagnose complex faults accurately.

It needs to prove that the complete workflow works from start to finish.

---

# Primary User Journey

The initial user journey will focus on a basic health check.

```text
1. The user opens PC Diagnostic Assistant.
2. The user selects Quick Health Check.
3. The application collects a basic system snapshot.
4. The application runs a small set of safe diagnostic checks.
5. The application creates evidence and findings.
6. The application creates cautious hypotheses where appropriate.
7. The application displays recommendations.
8. The result is saved as an Investigation.
9. The user can reopen the Investigation later.
```

This journey provides one complete vertical slice through the application architecture.

---

# Included Features

## Quick Health Check

The MVP will include a lightweight system scan.

The Quick Health Check should inspect a small number of common and low-risk system indicators.

Initial checks may include:

* Available storage space.
* Total and available memory.
* Operating system information.
* System uptime.
* Recent unexpected shutdown events, if practical.
* Basic processor information.
* Basic drive information.

The exact number of checks should remain limited.

The goal is to prove the diagnostic workflow rather than maximise hardware coverage.

---

## Basic System Snapshot

The application will capture a point-in-time snapshot of the system.

The first snapshot may include:

* Computer name.
* Windows version.
* System uptime.
* Processor name.
* Processor core count.
* Total memory.
* Available memory.
* Installed logical drives.
* Drive capacity.
* Drive free space.

The snapshot provides context for the health check and future investigation history.

---

## Initial Diagnostic Checks

The MVP should begin with checks that are:

* Safe.
* Easy to reproduce.
* Available through standard Windows or .NET capabilities.
* Easy to explain.
* Useful for validating the architecture.

The first implemented check should be:

### Low Storage Capacity

The application should detect when a drive has limited free space.

A possible diagnostic chain is:

```text
Diagnostic Check:
Measure available storage space.

Evidence:
The system drive has 8 GB of free space remaining.

Finding:
The system drive is running low on available space.

Hypothesis:
Limited storage capacity may affect Windows updates, temporary files,
application performance, or general system stability.

Recommendation:
Consider reviewing storage usage and freeing space.
Back up important data before removing files.
```

The threshold must be documented and should avoid presenting a normal condition as critical.

---

## Findings and Evidence

The application must clearly separate simplified findings from the technical evidence that supports them.

For each detected concern, the user should be able to see:

* What was checked.
* What was found.
* The exact evidence.
* What the application believes it may mean.
* The confidence level.
* The priority level.
* The recommended next area of investigation.

This separation is a core part of the product and must be present in the MVP.

---

## Investigations

Each Quick Health Check result will create an Investigation.

An MVP Investigation should contain:

* A title.
* A reason for creation.
* Creation date and time.
* Status.
* System snapshot.
* Findings.
* Evidence.
* Hypotheses.
* Recommendations.
* Basic notes.
* Investigation history.

The first version does not require advanced branching diagnostic workflows.

The Investigation primarily acts as a saved and reviewable diagnostic record.

---

## Basic Investigation History

The application should record important actions.

Initial history entries may include:

* Investigation created.
* Quick Health Check started.
* System snapshot completed.
* Diagnostic check completed.
* Finding created.
* Scan completed.
* Investigation reopened.
* User note added.

A complete event-sourcing system is not required.

A simple ordered history is sufficient for the MVP.

---

## User Notes

Users should be able to add plain-text notes to an Investigation.

Notes provide immediate value because they allow users to record:

* Symptoms.
* Changes made to the system.
* Tests completed outside the application.
* Observations.
* Follow-up actions.

The first version does not require rich-text editing, attachments, or advanced organisation.

---

## Save and Reopen Investigations

The MVP must support local persistence.

Users should be able to:

* Save an Investigation.
* View previously saved Investigations.
* Reopen an Investigation.
* Review its snapshot, findings, evidence, recommendations, and notes.

The exact persistence technology will be chosen separately.

Cloud synchronisation is not part of the MVP.

---

## Basic Desktop Interface

The MVP will use a functional WPF interface.

The UI should prioritise clarity over visual polish.

The initial interface may contain:

* Home page.
* Quick Health Check action.
* Scan progress view.
* Results view.
* Investigation list.
* Investigation detail view.
* Notes input.
* Basic settings or application information where required.

The first version does not require complex animations, custom visualisations, or advanced theming.

---

## Logging and Error Handling

The MVP must include basic application logging and user-friendly error handling.

The application should:

* Log unexpected errors.
* Log failed diagnostic checks.
* Preserve successful check results when another check fails.
* Distinguish unavailable data from healthy data.
* Inform the user when a check could not be completed.

Raw exceptions should not be displayed directly in the user interface.

---

## Basic Automated Testing

The MVP should include automated tests for the highest-value logic.

Initial tests should cover:

* Low-storage evaluation.
* Evidence-to-finding behaviour.
* Investigation state changes.
* Partial scan failure.
* Saving and reopening investigations where practical.
* Priority and confidence assignment for implemented checks.

The goal is not complete test coverage.

The goal is to establish a professional testing approach from the beginning.

---

# MVP Diagnostic Model

The initial diagnostic pipeline will be:

```text
Quick Health Check Request
        ↓
Collect System Snapshot
        ↓
Run Supported Checks
        ↓
Create Evidence
        ↓
Create Findings
        ↓
Create or Update Hypotheses
        ↓
Generate Recommendations
        ↓
Save Investigation
        ↓
Display Results
```

The first version should implement this pipeline with only a small number of checks.

Adding more checks should not be used as a substitute for completing and validating the full workflow.

---

# Recommended Initial Checks

The MVP should begin with no more than three or four checks.

A suitable initial set is:

## 1. Low Storage Capacity

Detect drives with low remaining space.

This should be the first vertical slice.

## 2. High Memory Pressure

Detect when available memory is unusually low at the time of the scan.

The result should be presented as a point-in-time observation, not proof of a memory fault.

## 3. Recent Unexpected Shutdowns

Inspect supported Windows event information for recent unexpected shutdowns.

This check may be postponed if Event Viewer integration introduces too much complexity during the first vertical slice.

## 4. Extended System Uptime

Identify unusually long uptime as an informational finding where a restart may be relevant to troubleshooting.

This should not be treated as a fault by itself.

These checks provide enough variety to validate storage, memory, event, and contextual diagnostic behaviour without attempting full hardware diagnosis.

---

# Explicitly Excluded From the MVP

The following features are outside the first release.

## Advanced Guided Diagnostics

The MVP will not initially include complete symptom-based workflows for:

* Crashes.
* Black screens.
* Blue screens.
* Network faults.
* Overheating.
* Startup failures.
* Driver faults.

These remain core long-term features but should be introduced after the base investigation workflow is stable.

---

## Full Diagnostic Scan

A complete system-wide diagnostic scan is not required for the first release.

The MVP Quick Health Check will establish the foundation needed for it.

---

## Advanced Hardware Monitoring

The MVP will not include:

* GPU temperature monitoring.
* CPU temperature monitoring.
* Fan-speed monitoring.
* Voltage monitoring.
* Thermal throttling detection.
* Vendor-specific hardware sensors.

These features require additional libraries, hardware support, and careful validation.

---

## SMART and Advanced Storage Health

The MVP will not initially include:

* Full SMART attribute interpretation.
* NVMe health-log analysis.
* Drive-failure prediction.
* Storage-controller diagnosis.
* Motherboard-slot diagnosis.

Basic capacity and drive information are sufficient for the first version.

---

## Repair Automation

The MVP will not:

* Run Command Prompt or PowerShell repair commands.
* Modify the registry.
* Install or remove drivers.
* Change Windows services.
* Alter startup applications.
* Run disk repairs.
* Apply fixes automatically.

This exclusion is permanent unless the product philosophy is intentionally changed.

---

## Advanced Reporting

The MVP does not require:

* PDF export.
* Branded reports.
* Report comparison.
* Charts.
* Customer-facing service reports.
* Digital signatures.

A simple structured export format may be added after saved Investigations are working reliably.

---

## User Accounts and Cloud Features

The MVP will not include:

* User registration.
* Login.
* Cloud storage.
* Cross-device synchronisation.
* Online profiles.
* Remote diagnostics.
* Telemetry requiring user accounts.

The application should remain local-first.

---

## Plugin System

The MVP will not include external diagnostic plugins or third-party extensions.

A plugin system would introduce significant complexity before the application has enough stable diagnostic contracts to support one responsibly.

---

# MVP Success Criteria

The MVP will be considered successful when all of the following are true:

1. A user can launch the application and run a Quick Health Check.
2. The application can collect a basic system snapshot.
3. At least one real diagnostic check produces evidence.
4. Evidence is converted into a user-understandable finding.
5. A cautious hypothesis and recommendation can be displayed.
6. Failed or unavailable checks are reported honestly.
7. The result is stored as an Investigation.
8. The Investigation can be reopened.
9. The user can add and save notes.
10. Core diagnostic logic has automated tests.
11. The user interface remains responsive while the scan runs.
12. The application does not perform any repair or irreversible action.

The MVP is not successful merely because it displays system information.

It must demonstrate the complete diagnostic workflow.

---

# Definition of Done

A feature is considered complete when:

* Its behaviour matches the documented requirement.
* Its responsibilities follow the architecture.
* Expected failures are handled.
* User-facing text avoids unsupported certainty.
* Relevant diagnostic reasoning has automated tests.
* Logging is included where useful.
* Documentation is updated.
* The feature has been manually tested on a supported Windows system.
* The implementation is committed with a clear and focused Git history.

---

# Development Approach

The MVP should be developed through small vertical slices.

Recommended order:

1. Create the solution and project structure.
2. Implement the core Investigation domain model.
3. Build the basic WPF application shell.
4. Implement the low-storage check through every layer.
5. Display the result.
6. Save and reopen the Investigation.
7. Add notes and basic history.
8. Add one additional diagnostic check.
9. Improve error handling and logging.
10. Review the MVP against the success criteria.

The team should resist adding advanced diagnostic features until the initial workflow is complete and reliable.

---

# Future Expansion

Once the MVP is stable, future milestones may introduce:

* Guided investigations.
* Multiple hypotheses per investigation.
* User-performed diagnostic checklists.
* Re-testing and confidence updates.
* Quick, full, and targeted scan modes.
* Event Viewer analysis.
* Hardware sensor integration.
* SMART and NVMe health data.
* Network diagnostics.
* Process and startup analysis.
* Exportable diagnostic reports.
* Comparison between system snapshots.
* Search-friendly recommendations.
* Investigation exhaustion and escalation workflows.

These features should be introduced incrementally and evaluated against the project’s design principles.

---

# Summary

The MVP will prove the central idea of PC Diagnostic Assistant through one complete, usable diagnostic workflow.

It will prioritise:

* A functional Quick Health Check.
* Clear separation between evidence, findings, and hypotheses.
* Saved Investigations.
* Transparent recommendations.
* Reliable error handling.
* A small number of well-implemented checks.

The MVP should be judged by whether it creates a solid foundation for guided diagnosis, not by the number of diagnostic features it contains.
