# MOSIP Architecture

## Design choices

The MOSIP architecture decisions have been based on the [Guiding Principles](Architecture-Principles.md) defined in the charter. The design choices are in line with the need for modularity, loose coupling and scalability of its components, and being API first.

* Micro-service based architecture for all platform services for modularity and scalability.
* Staged Event Driven Architecture (SEDA) for processing Registration data for extensibility.
* Thick client architecture for the registration client to support offline operations as well as process security.

The sections below provide different views of the logical architecture of MOSIP.

## Functional Architecture

From a MOSIP perspective, several actors are involved in the ID system.

* The **Individual** or the **Resident** is at the centre of it all. It is their identity that the system deals with.
* The **Officer** is a representative of the ID issuer. There are several specialized roles for the officer.
  * The **Operator** assists the individual during registration.
  * The **Supervisor** verifies and attests exceptional cases in registration.
  * The **Adjudicator** carries out manual verification or comparison of an individual's data in the ID issue process.
  * The **Auditor** performs an audit or forensic analysis of specific enrollments.
  * The **Administrator** is a super user who manages the configuration data of the system.
* The **Partner** represents a 3rd party service or application that interacts with MOSIP. There are specialized partners in the ecosystem.
  * The **Relying Party** is an **Authentication Partner** who relies on the ID system for their business transaction. This could be a social scheme for benefits disbursement or a bank for opening accounts.
  * The **Credential Provider** is a print service provider for the credential issue.
  * The **Device Provider** is a partner who provides biometric devices.
  * The **FTM Provider** is a partner that provides foundational trust modules for devices.
  * The **Partner Application** is a system that relies on mosip or one that mosip relies on. This could be a CRVS system or a Functional ID system such as a Passport or a driver's License.
  * The **ID System** is a system that mosip integrates with for inter-operable ID

The diagram shows the functional architecture of mosip with the actors.

![](<\_images/arch\_diagrams/mosip\_functional\_architecture\_v1 (1).png>)

## Modular Architecture

Mosip has several modules that offer related functionality. These include the core modules of

* Pre-registration
* Registration client
* Registration processor
* ID Repository
* Authentication
* Resident Services

and the support modules

* Partner Management
* Administration
* Reporting

**Note**: All user interface modules are reference implementations and can be used as is, refactored or customized or replaced with alternative implementations in the actual deployment.

The diagram below shows the various modules of mosip with their respective service bouquets and their interaction.

![](<\_images/arch\_diagrams/mosip\_logical\_architecture\_v1 (1).png>)