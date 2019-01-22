## Turbot Concepts
Turbot provides enterprise guardrails for Amazon Web Services.

This document outlines the beliefs, models and assumptions Turbot has defined
to create those guardrails - providing organizations with a working balance
between agility and compliance. Please see [other help sections](http://help.github.com) for
implementation specifics and how to guides.

## Design Beliefs
Balancing agility with controls requires a clear and simple set of beliefs
guiding our designs and trade-off decisions. This section outlines how
Turbot thinks about Enterprise Controls for Cloud Infrastructure.

#### Cloud Infrastructure is managed dynamically by Applications & DevOps Teams.
Cloud Infrastructure is designed to be changed in real time,
providing scalability and reliability in Production and flexibility in
Development. Enterprises moving to Cloud Infrastructure need to give control of
Application Infrastructure to the Application and its DevOps Teams.

#### Enterprises run many different Applications.
Each Enterprise consists of many Applications, each with a specific purpose,
requirements and controls. Applications may interact, or be dependent on each
other, but are managed (e.g. access, change control) as separate systems.

#### Applications have multiple Environments.
Multiple copies and environments of each Application are required to support
Development, Quality Assurance and Production activities. These Environments
should be similar, but are separate systems that require different levels of
access, reliability and control.

#### Each Application & Application Environment is managed differently.
Production needs more control than Development. Customer data and compliance
records data needs more protection than basic organization information.
Critical systems need close monitoring, while small applications can fail
without impact. Each Application Environment needs to be managed according
to its needs, providing agility and control in the right places.

#### Applications are Independent, but connected.
Although Applications function separately, they are often integrated and always
have some level of shared citizenship in the Enterprise Network.

#### Enterprises require common Controls across Applications.
The Enterprise Network shares many Application Environments, so central rules
and control are required to protect the whole. So, certain Enterprise policies
and requirements apply to all applications and must be centrally managed. For
example, data protection, access control and network firewalls.

## Cluster of Accounts
Each Organization can run 1 or more Turbot Clusters. A Cluster defines Access,
Controls and Configuration that apply to all Accounts across the Organization.
It is typically managed by a central Cloud Infrastructure DevOps team.

Each Cluster manages 1 or more Accounts. Each Account consists of AWS
infrastructure, Windows servers, Linux servers, Databases, etc. It is typically
managed by an Application Team.

The Cluster provides guardrails and accelerated setup for Applications,
including:

Enterprise policies (e.g. Server hardening, Service availability)
Best practice settings (e.g. Monitoring)
Integration points with Enterprise systems (e.g. LDAP, Helpdesk).
Central administration, access and reporting.

While Applications manage their own resources within the Cluster guardrails:

Servers
Databases
Access and Permissions
Self-service administration and reporting.

## Authentication, Access & Permissions
### Authentication
Turbot supports multiple methods of authentication, including LDAP and Turbot
local username/passwords. Ultimately, each method of authentication maps to a
verified email address of the user.

Each Cluster may specify through options which Authentication methods it
supports. For example, Cluster A may specify that authentication MUST be
through LDAP, while Cluster B may allow authentication through Turbot managed
users.
