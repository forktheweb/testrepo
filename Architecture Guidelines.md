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

### Diagrams

The following diagrams must be included in your architecture document:
 
| Type | Description |
|---|---|
| _Component Diagram_ | What are the system functions and how do they interact |
| _Physical Diagram_ | Where will the component be deployed |
| _Security Diagram_ | authc, authz, trust relationships, auditing as defined in [Security Architecture Standards](./Security%20Architecture%20Standards.md) |

### How do I make the diagrams?


##### Example:
![Component](https://www.plantuml.com/plantuml/svg/ZP4z3y8W48PtVyMbpaHc1rCTs5pis30WlHZI3mn7QupnlmisKLeJzPRZuytplWSvUULytpOBUDLPwLgT4BAzqSuIki5eX5qMhcw9x5bbcsZOKG8iEHU2yrHu_mdVPZFqbAlaY1LYAZeWsTvf99cSfsvlky9R5nV5bJosSpieE_GNwsf6eqvEyyVTzz53HCOsd--n1krGUQHLXGt6Rhh1raZ_uUQn0YzEWXHQe4P8ZbqLFl01)

<details><summary>Show UML Code</summary>
<p>
  
```
@startuml
    package "Microservice B"   {
       [microservice-b]  #00FF00
    }
    package "Microservice A" {
        [microservice-a] #00FFFF
        [Resources]
    }
    package "Storage System" {
        [network-storage]
    }

       
    [microservice-a] --> [microservice-b] : creates/deletes/invokes
    [microservice-a] --> [network-storage] : Stores State

   @enduml
```
</p>
</details>

##### Instructions:

1. Visit [PlantText](https://www.planttext.com/)
2. Write UML code
3. Embed SVG as `![Component](--SVG URL --)`
