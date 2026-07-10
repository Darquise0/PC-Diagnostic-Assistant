# PC Diagnostic Assistant

> An evidence-based Windows diagnostic assistant that helps users investigate hardware and software issues through structured diagnostic workflows.

> [!IMPORTANT]
> **Project Status**
>
> PC Diagnostic Assistant is currently in active development.
>
> The project is following a documentation-first approach, meaning the architecture, product design, and engineering decisions are being established before implementation begins.
>
> While the application is still in its early stages, the goal is to build a production-quality, open-source Windows diagnostic assistant through incremental, well-tested development.
>
> The latest progress, roadmap, and design decisions can be found in the `/docs` directory.

PC Diagnostic Assistant is an open-source Windows desktop application designed to simplify PC troubleshooting by bringing together diagnostic information, evidence, and guided investigations into a single application.


Rather than acting as another system information viewer, the project aims to organise the diagnostic process itself. It helps users collect evidence, understand what it means, track their progress, and narrow down likely causes while leaving repair decisions entirely in the hands of the user.

---

# Why?

Troubleshooting Windows PCs often requires jumping between multiple built-in tools and third-party utilities such as:

* Task Manager
* Event Viewer
* Device Manager
* Resource Monitor
* Settings
* Command Prompt
* Hardware monitoring software

This fragmented workflow makes it difficult to collect evidence, keep track of previous investigations, and decide what to test next.

PC Diagnostic Assistant aims to solve this by providing a structured diagnostic workflow that keeps everything in one place.

---

# Project Goals

The primary goals of this project are to:

* Simplify Windows PC diagnostics.
* Reduce context switching between multiple diagnostic tools.
* Organise troubleshooting into structured investigations.
* Present evidence before conclusions.
* Help users understand what diagnostic information actually means.
* Encourage safe, evidence-based troubleshooting.

The application assists users in identifying likely causes of problems but does **not** perform repairs or make changes to the operating system.

---

# Planned Features

The long-term vision includes support for features such as:

* Quick Health Checks
* Full Diagnostic Scans
* Guided Investigations
* Investigation History
* System Snapshots
* Hardware & Software Diagnostics
* Event Viewer Analysis
* Storage Diagnostics
* Network Diagnostics
* Exportable Investigation Reports
* User Notes
* Confidence-Based Recommendations
* Re-testing Workflows

Features will be introduced incrementally as the project evolves.

---

# Engineering Goals

This project is also intended to demonstrate professional software engineering practices, including:

* Object-Oriented Programming
* SOLID Principles
* Layered Architecture
* MVVM
* Dependency Injection
* Async Programming
* Automated Testing
* Logging
* Clean Git History
* Documentation-First Development

The focus is on building maintainable software rather than simply producing a working application.

---

# Technology Stack

Current technology decisions include:

* .NET 10 (LTS)
* WPF
* CommunityToolkit.Mvvm
* Microsoft Dependency Injection
* Microsoft Configuration
* Microsoft Logging
* Serilog
* SQLite
* Entity Framework Core

Additional implementation decisions will be documented as development progresses.

---

# Documentation

This project follows a documentation-first approach.

Project documentation can be found in the `/docs` directory.

Current documentation includes:

* Product Vision
* Domain Model
* Architecture
* Design Principles
* MVP Scope
* Technology Stack
* Roadmap

These documents explain the reasoning behind the project's design decisions and will continue to evolve alongside the application.

---

# Current Status

**Current Phase:** Planning & Design

The architectural foundation and project documentation are currently being completed before implementation begins.

The first development milestone will focus on establishing the solution structure and implementing the first end-to-end vertical slice of the application.

---

# Contributing

Contributions, ideas, and constructive feedback are always welcome.

As the project is still in its early stages, architectural consistency and adherence to the documented design principles are prioritised over rapid feature development.

Please review the documentation before opening feature requests or submitting pull requests.

---

# License

This project is licensed under the MIT License.

See the `LICENSE` file for more information.

