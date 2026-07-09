# RASD_DD_project
RASD &amp; DD for Best Bike Paths: a software system for GPS trip recording, sensor-based path status detection, and multi-user path scoring. UML + Alloy formal modeling. SE2 @ PoliMi 2025/26.
# Best Bike Paths — Requirements & Design Project

<p align="center">
  <img src="https://img.shields.io/badge/Politecnico%20di%20Milano-003576?style=for-the-badge&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCIgZmlsbD0id2hpdGUiPjxwYXRoIGQ9Ik0xMiAzTDEgOWwxMSA2IDkgLTQuOVYxN2gyVjlNNSAxMy4xOFY3TDEyIDIzbDcgLTMuODJWMTMuMThMMTIgMTdMNSAxMy4xOFoiLz48L3N2Zz4=" alt="Politecnico di Milano"/>
  <img src="https://img.shields.io/badge/Course-Software%20Engineering%202-blue?style=for-the-badge" alt="SE2"/>
  <img src="https://img.shields.io/badge/A.Y.-2025%2F2026-green?style=for-the-badge" alt="Academic Year"/>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/UML-Modeling-orange?style=flat-square" alt="UML"/>
  <img src="https://img.shields.io/badge/Alloy-Formal%20Analysis-red?style=flat-square" alt="Alloy"/>
  <img src="https://img.shields.io/badge/Documentation-LaTeX-008080?style=flat-square" alt="LaTeX"/>
  <img src="https://img.shields.io/badge/Status-Completed-brightgreen?style=flat-square" alt="Status"/>
</p>

---

> Requirements Analysis and Specification Document (RASD) and Design Document (DD) for **Best Bike Paths (BBP)**, a software system that lets cyclists record trips and collaboratively build a community-driven inventory of bike paths.
>
> Academic project developed for the **Software Engineering 2** course — Politecnico di Milano, A.Y. 2025/2026.

---

## 📖 Table of contents

- [Overview](#overview)
- [Deliverables](#deliverables)
- [Domain model](#domain-model)
- [Use cases](#use-cases)
- [Architecture](#architecture)
- [Formal modeling with Alloy](#formal-modeling-with-alloy)
- [Methodology and tools](#methodology-and-tools)
- [Problem scope](#problem-scope)
- [Authors](#authors)
- [License](#license)

---

## Overview

Best Bike Paths (BBP) is a system that supports cyclists in two complementary ways:

- **Recording personal trips** — GPS-tracked rides with statistics (distance, average speed, performance metrics) enriched with weather data from an external service.
- **Building a shared inventory of bike paths** — users contribute publishable information about path status (optimal, medium, sufficient, requires maintenance) and obstacles such as potholes, either manually or through automated acquisition from mobile sensors (GPS, accelerometer, gyroscope).

Any user, registered or not, can query the system by specifying origin and destination and visualize the available bike paths on a map, ranked by a score that combines path status and routing effectiveness.

This repository contains the full engineering documentation produced for the project: the **RASD**, which formalizes the problem, and the **DD**, which defines the software architecture designed to satisfy it.


---

## Deliverables

### 📄 RASD — Requirements Analysis and Specification Document

Following the IEEE-inspired structure recommended by the course, the RASD covers:

- **Introduction** — purpose, scope, world and shared phenomena, glossary.
- **Overall description** — scenarios, domain model, product functions, user characteristics, and domain assumptions.
- **Specific requirements** — external interfaces, functional requirements formalized through use case diagrams and use cases with sequence/activity diagrams, plus non-functional requirements (performance, reliability, availability, security, maintainability, portability).
- **Formal analysis using Alloy** — a formal model validated through the Alloy Analyzer, including generated worlds and assertion checks that demonstrate the soundness of key properties of the specification.

📎 [Read the full RASD](RASD_softeng2.pdf)

### 📐 DD — Design Document

The Design Document translates the specified requirements into a concrete software architecture:

- **Architectural design** — high-level overview, component view, deployment view, runtime view (component interactions via sequence diagrams), component interfaces, and the architectural styles and patterns adopted (with rationale).
- **User interface design** — mockups and navigation flow.
- **Requirements traceability** — explicit mapping between requirements defined in the RASD and design elements in the DD.
- **Implementation, integration, and test plan** — proposed order for implementing subcomponents, integrating them, and testing the integration.

📎 [Read the full DD](DD_softeng2.pdf)

---

## Domain model

The domain model captures the key entities of the world targeted by BBP — users, trips, bike paths, path segments, status reports, and their relationships — together with the constraints that regulate them.

<p align="center">
  <img src="assets/domain-model.png" alt="Domain model — class diagram" width="720"/>
</p>

State diagrams complement the class model by describing how a bike path's status evolves as new reports are submitted and merged.

<p align="center">
  <img src="assets/path-state-diagram.png" alt="Bike path state diagram" width="520"/>
</p>

---

## Use cases

The functional requirements are organized around the main actors of the system: **guest users**, **registered users**, and the **external weather service**.

<p align="center">
  <img src="assets/use-case-diagram.png" alt="Use case diagram" width="720"/>
</p>

Each use case is refined through sequence or activity diagrams. Below, the flow for the **automated insertion of path information** while the user is biking:

<p align="center">
  <img src="assets/sequence-automated-insertion.png" alt="Sequence diagram — automated path insertion" width="720"/>
</p>

---

## Architecture

BBP is designed as a distributed system with a mobile client, a backend orchestrating business logic and data persistence, and integrations with external services (map provider, weather API).

### Component view

<p align="center">
  <img src="assets/component-view.png" alt="Component view" width="720"/>
</p>

### Deployment view

<p align="center">
  <img src="assets/deployment-view.png" alt="Deployment view" width="720"/>
</p>

### Runtime view

Sequence diagrams describe how components collaborate to fulfill the main use cases — for example, computing and visualizing the best paths between two points.

<p align="center">
  <img src="assets/runtime-view.png" alt="Runtime view — path visualization" width="720"/>
</p>

---

## Formal modeling with Alloy

An Alloy model was built to formally capture the core invariants of the BBP world — for instance, the well-formedness of paths, the consistency of merged status reports, and the freshness-based rules that govern which report prevails. The model was validated through the Alloy Analyzer by generating example worlds and checking assertions on the properties of interest.

<p align="center">
  <img src="assets/alloy-world.png" alt="Alloy — generated world" width="720"/>
</p>

---

## Methodology and tools

- **Modeling notations:** UML (class, state, use case, sequence, activity, component, deployment diagrams) and Alloy for formal specification.
- **Formal verification:** Alloy Analyzer, used to explore generated worlds and check assertions on critical properties of the model.
- **Documentation:** Overleaf with version-controlled sources.

---

## Problem scope

The scope tackled in this project reflects the group configuration required by the assignment.


- Recording of personal trips
- Insertion of publishable information in manual mode
- Visualization of possible paths between an origin and a destination
- Insertion of publishable information in automated mode with user confirmation
- Merging of inormation incoming from different users based on freshness and confirmations

---

## Authors

- **Isabel Reguera** — [isabel.reguera@mail.polimi.it] 
- **Michelangelo Spandri** — [michelangelo.spandri@mail.polimi.it]
- **Raffaele Rizzuti** — [raffaele.rizzuti@mail.polimi.it]
---

## License

This project is released for academic and educational purposes. All rights reserved to the authors.

---

## Acknowledgements

Project developed for the **Software Engineering 2** course held at Politecnico di Milano, A.Y. 2025/2026, under the supervision of the course professors.
