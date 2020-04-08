# CrateKube Architecture Guidelines


## Introduction
This document is designed to provide a set of guidelines for contributors to architect new CrateKube features.  New 
contributors and developers who are unfamiliar with our architecture document format can refer here before submitting proposals.

## Who is this for?
All developers and contributors who are going to architect new features on the CrateKube open source project.

## Document Format
Each architecture document should contain:

- An Overview
- List of components and their short descriptions (1-2 paragraphs)
- [MVaP](https://www.toptal.com/designers/product-design/minimum-valuable-product) functionality expectations
- Diagrams
  - Component Diagram:  what are the system functions and how do they interact
  - Physical Diagram:  where will the component be deployed
  - Security Diagram:  authc, authz, trust relationships, auditing as defined in [Crate Security Architecture Standards](./Security%20Architecture%20Standards.md)
 
