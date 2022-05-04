
![OASIS Logo](http://docs.oasis-open.org/templates/OASISLogo-v3.0.png)

-------

# OpenC2 Actuator Profile for Posture Attribute Collection Version 1.0

## Committee Specification Draft 01

## xx May 2022

&nbsp;

<!-- URI list start (commented out except during publication by OASIS TC Admin)

#### This stage:
https://docs.oasis-open.org/openc2/ap-pac/v1.0/csd01/ap-pac-v1.0-csd01.md (Authoritative) \
https://docs.oasis-open.org/openc2/ap-pac/v1.0/csd01/ap-pac-v1.0-csd01.html \
https://docs.oasis-open.org/openc2/ap-pac/v1.0/csd01/ap-pac-v1.0-csd01.pdf

#### Previous stage:
N/A

#### Latest stage:
https://docs.oasis-open.org/openc2/ap-pac/v1.0/ap-pac-v1.0.md (Authoritative) \
https://docs.oasis-open.org/openc2/ap-pac/v1.0/ap-pac-v1.0.html \
https://docs.oasis-open.org/openc2/ap-pac/v1.0/ap-pac-v1.0.pdf

URI list end (commented out except during publication by OASIS TC Admin) -->

#### Technical Committee:
[OASIS Open Command and Control (OpenC2) TC](https://www.oasis-open.org/committees/openc2/)

#### Chair:
Duncan Sparrell (duncan@sfractal.com), [sFractal Consulting LLC](http://www.sfractal.com/) \
Michael Rosa (mjrosa@cyber.nsa.gov), [National Security Agency](http://www.nsa.gov/)

#### Editors:
David Lemire (david.lemire@hii-tsd), [National Security Agency](http://www.nsa.gov/)
David Kemp (d.kemp@cyber.nsa.gov), [National Security Agency](http://www.nsa.gov/)

#### Additional artifacts:
This prose specification is one component of a Work Product that also includes:
* XML schemas: (list file names or directory name)
* Other parts (list titles and/or file names)
* `(Note: Any normative computer language definitions that are
  part of the Work Product, such as XML instances, schemas and
  Java(TM) code, including fragments of such, must be (a) well
  formed and valid, (b) provided in separate plain text files,
  (c) referenced from the Work Product; and (d) where any
  definition in these separate files disagrees with the
  definition found in the specification, the definition in the
  separate file prevails. Remove this note before submitting for
  publication.)`

#### Related work:
This specification is related to:
* _Open Command and Control (OpenC2) Language Specification
  Version 1.0_. Edited by Jason Romano and Duncan Sparrell.
  Latest stage:
  https://docs.oasis-open.org/openc2/oc2ls/v1.0/oc2ls-v1.0.html.

#### Abstract:
This specification defines an actuator profile to automate
collection of security posture attributes from virtual and
physical computing resources using OpenC2. Security Posture
Attribute Collection (PAC) supports security automation by
providing mechanisms to collect and aggregate the configuration
and status of network components for use in situational
awareness, security posture evaluation, and response actions.
This actuator profile defines the OpenC2 Actions, Targets,
Arguments, and Specifiers along with conformance clauses to
enable the operation of OpenC2 Producers and Consumers in the
context of PAC. It covers identification of computing resources,
definition of security-relevant resource attributes, and
controlling the collection of those attributes using direct pull
or event-based push mechanisms.

Open Command and Control (OpenC2) is an effort to rigorously
standardize command and control of vital cyber defense systems.
OpenC2 is a concise and extensible language to enable the command
and control of cyber defense components, subsystems and/or
systems in a manner that is agnostic of the underlying products,
technologies, transport mechanisms or other aspects of the
implementation.

#### Status:
This document was last revised or approved by the OASIS Open
Command and Control (OpenC2) TC on the above date. The level of
approval is also listed above. Check the "Latest stage" location
noted above for possible later revisions of this document. Any
other numbered Versions and other technical work produced by the
Technical Committee (TC) are listed at
https://www.oasis-open.org/committees/tc_home.php?wg_abbrev=openc2#technical.

TC members should send comments on this specification to the TC's
email list. Others should send comments to the TC's public
comment list, after subscribing to it by following the
instructions at the "[Send A
Comment](https://www.oasis-open.org/committees/comments/index.php?wg_abbrev=)"
button on the TC's web page at
https://www.oasis-open.org/committees/openc2/.

This specification is provided under the
[Non-Assertion](https://www.oasis-open.org/policies-guidelines/ipr/#Non-Assertion-Mode)
Mode of the OASIS IPR Policy, the mode chosen when the Technical
Committee was established. For information on whether any patents
have been disclosed that may be essential to implementing this
specification, and any offers of patent licensing terms, please
refer to the Intellectual Property Rights section of the TC's web
page (https://www.oasis-open.org/committees/openc2/ipr.php).

Note that any machine-readable content ([Computer Language
Definitions](https://www.oasis-open.org/policies-guidelines/tc-process-2017-05-26/#wpComponentsCompLang))
declared Normative for this Work Product is provided in separate
plain text files. In the event of a discrepancy between any such
plain text file and display content in the Work Product's prose
narrative document(s), the content in the separate plain text
file prevails.

#### Key words:
The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL
NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED",
"MAY", and "OPTIONAL" in this document are to be interpreted as
described in BCP 14 [[RFC2119](#rfc2119)] and
[[RFC8174](#rfc8174)] when, and only when, they appear in all
capitals, as shown here.

#### Citation format:
When referencing this specification the following citation format
should be used:

**[AP-PAC-v1.0]**

_OpenC2 Actuator Profile for Posture Attribute Collection Version
1.0_. Edited by David Lemire and David Kemp. 30 March 2022. OASIS
Committee Specification Draft 01.
https://docs.oasis-open.org/openc2/ap-pac/v1.0/csd01/ap-pac-v1.0-csd01.html.
Latest stage:
https://docs.oasis-open.org/openc2/ap-pac/v1.0/ap-pac-v1.0.html.

#### Notices
Copyright © OASIS Open 2022. All Rights Reserved.

Distributed under the terms of the OASIS [IPR
Policy](https://www.oasis-open.org/policies-guidelines/ipr/).

The name "OASIS" is a trademark of
[OASIS](https://www.oasis-open.org/), the owner and developer of
this specification, and should be used only to refer to the
organization and its official outputs.

For complete copyright information please see the full Notices
section in an Appendix below.

-------

# Table of Contents
[[TOC will be inserted here]]

-------

# 1 Introduction

*The content in this section is non-normative, except where it is
marked normative.*

**Note:** This Actuator profile is consistent with Version 1.0 of
the OpenC2 Language Specification
[\[OpenC2-Lang-v1.0\]](#openc2-lang-v1.0).

OpenC2 is a suite of specifications that enables command and
control of cyber defense systems and components. OpenC2 typically
uses a request-response paradigm where a Command is encoded by a
Producer (managing application) and transferred to a Consumer
(managed device or virtualized function) using a secure transfer
protocol, and the Consumer acts on the request and responds with
status and any other requested information.

This specification defines an Actuator profile for **Posture
Attribute Collection (PAC)**. In particular, the specification
comprises a set of Actions, Targets and Target Specifiers,
Command Arguments, and Actuator Specifiers that integrates PAC
functionality with the OpenC2 Command set. Through this Command
set, cyber security orchestrators may gain visibility into and
provide control over PAC in a manner that is independent of the
instance of the PAC function.

All components, devices, and systems that provide PAC
functionality MUST implement the identified OpenC2 Actions,
Targets, Specifiers, and Arguments as specified in the
Conformance section of this specification.

Though cyber defense components, devices, systems and/or
instances may implement multiple Actuator profiles, a particular
OpenC2 Message may reference at most a single Actuator profile.
The scope of this document is limited to PAC.

The rest of the specification is organized as follows:

The remaining of Section 1 includes information about the IPR
policy, terminology used, and document conventions pertinent to
this Actuator profile specification.

[Section 2](#2-section-heading) (normative) binds this particular
profile to Version 1.0 of the OpenC2 Language Specification
[\[OpenC2-Lang-v1.0\]](#openc2-lang-v1.0). It enumerates the
components of the Language Specification that are meaningful in
the context of PAC and defines components that are applicable to
this distinct profile. In addition, Section 2 defines the
Commands (i.e., the Action/Target pairs, arguments, and
associated specifiers) that are permitted in the context of PAC.

[Section 3](#3-conformance) (normative) presents definitive
criteria for conformance so that cyber security stakeholders can
be assured that their products, instances and/or integrations are
compatible with this profile (OpenC2 Actuator Profile for Posture
Attribute Collection Version 1.0).

[Appendix E](#appendix-e-orchestrator-consumer-operating-model)
(non-normative) describes the operating model for an
"Orchestrator Consumer", an OpenC2 element that can receive
commands from a higher-level ("upstream") Producer and then
command lower-level ("downstream") Consumers to implement those
commands.

[Appendix F](#appendix-f-example-appendix-with-subsections) (non-normative)
provides multiple examples of Commands and associated Responses
(JSON serialization).

## 1.1 Changes from earlier versions

This is the initial version of this specifciation.
<!-- Optional section -->

## 1.2 Glossary

### 1.2.1 Definitions of terms

*This section is normative.*

-   **Action**: The task or activity to be performed (e.g.,
    'deny').

-   **Actuator**: The function performed by the Consumer that
    executes the Command (e.g., 'Posture Attribute Collection').

-   **Argument**: A property of a Command that provides
    additional information on how to perform the Command, such as
    date/time, periodicity, duration, etc.

-   **Command**: A Message defined by an Action-Target pair that
    is sent from a Producer and received by a Consumer.

-   **Consumer**: A managed device / application that receives
    Commands. Note that a single device / application can have
    both Consumer and Producer capabilities.

-   **Message**: A content- and transport-independent set of
    elements conveyed between Consumers and Producers.

-   **Producer**: A manager application that sends Commands.

-   **Response**: A Message from a Consumer to a Producer
    acknowledging a Command or returning the requested resources
    or status to a previously received Command.

-   **Specifier**: A property or field that identifies a Target
    or Actuator to some level of precision.

-   **Target**: The object of the Action, i.e., the Action is
    performed on the Target (e.g., IP Address).

### 1.2.2 Acronyms and abbreviations

TBSL

### 1.2.3 Document conventions

#### 1.2.3.1 Naming Conventions

-   [\[RFC2119\]](#rfc2119)/[\[RFC8174\]](\l) key words are in
    all uppercase.

-   All property names and literals are in lowercase, except when
    referencing canonical names defined in another standard
    (e.g., literal values from an IANA registry).

-   Words in property names are separated with an underscore
    (\_), while words in string enumerations and type names are
    separated with a hyphen (-).

-   The term "hyphen" used here refers to the ASCII hyphen or
    minus character, which in Unicode is "hyphen-minus", U+002D.

#### 1.2.3.2 Font Colors and Style

The following color, font and font style conventions are used in
this document:

-   A fixed width font is used for all type names, property
    names, and literals.

-   Property names are in bold style – **'created\_at'**.

-   All examples in this document are expressed in JSON. They are
    in fixed width font, with straight quotes, black text and a
    light shaded background, and 4-space indentation. JSON
    examples in this document are representations of JSON
    Objects. They should not be interpreted as string literals.
    The ordering of object keys is insignificant. Whitespace
    before or after JSON structural characters in the examples
    are insignificant [\[RFC8259\]](#rfc8259).

-   Parts of the example may be omitted for conciseness and
    clarity.
    > These omitted parts are denoted with ellipses (...).

Example:

```
{
  "action": "deny",
  "target": {
    "file": {
      "hashes": {
        "sha256": "22fe72a34f006ea67d26bb7004e2b6941b5c3953d43ae7ec24d41b1a928a6973"
      }
    }
  }
}
```

-------

# 2 OpenC2 Language Binding

*This section is normative.*

This section defines the set of Actions, Targets, Arguments, and
Actuator Specifiers that are meaningful in the context of PAC and
the appropriate status codes, status texts, and other properties
of a Response message. In addition, this section defines the
Commands allowed by this Actuator profile. Section 2 is organized
into three major subsections; [Command
Components](#21-openc2-command-components), [Response
Components](#22-openc2-response-components), and
[Commands](#23-openc2-commands).

Extensions to the Language Specification are defined in
accordance with Version 1.0 of the [OpenC2 Language
Specification](#openc2-lang-v1.0), Section 3.1.4, where:

1.  The unique name of the PAC schema is: `oasis-open.org/openc2/v1.0/ap-pac`

2.  The namespace identifier (NSID) referring to the PAC schema is: `pac`

3.  The conformance requirements for the OpenC2 Posture Attribute
    Collection Actuator profile are defined and included in this
    document.

## 2.1 OpenC2 Command Components

The components of an OpenC2 Command include Actions, Targets,
Actuators and associated Arguments and Specifiers. Appropriate
aggregation of the components will define a Command-body that is
meaningful in the context of PAC.

This specification identifies the applicable components of an
OpenC2 Command. The components of an OpenC2 Command include:

-   **Action:** A subset of the Actions defined in Version 1.0 of the
    [OpenC2 Language Specification](#openc2-lang-v1.0) that are
    meaningful in the context of a posture attribute collection.

    -   This profile SHALL NOT define Actions that are external
        to Version 1.0 of the [OpenC2 Language
        Specification](#openc2-lang-v1.0).

    -   This profile MAY augment the definition of the Actions in
        the context of PAC.

    -   This profile SHALL NOT define Actions in a manner that is
        inconsistent with Version 1.0 of the [OpenC2 Language
        Specification](#openc2-lang-v1.0).

-   **Target:** A subset of the Targets and Target-Specifiers defined
    in Version 1.0 of the [OpenC2 Language
    Specification](#openc2-lang-v1.0) that are meaningful in the
    context of PAC and two Targets and their Specifiers that are
    defined in this specification.

-   **Arguments:** A subset of the Arguments defined in Version 1.0
    of the [OpenC2 Language Specification](#openc2-lang-v1.0) and
    a set of Arguments defined in this specification.

-   **Actuator:** A set of Actuator Specifiers defined in this
    specification that are meaningful in the context of PAC.

### 2.1.1 Actions

Table 2.1.1-1 presents the Actions defined in Version 1.0 of the
OpenC2 Language Specification, which are meaningful in the
context of PAC. The particular Action/Target pairs that are valid
combinations are presented in [Section 2.3](#23-openc2-commands).

#### Table 2.1.1-1 Common Actions Applicable to PAC


### 2.1.2 Targets

Table 2.1.2-1 lists the Targets defined in Version 1.0 of the
OpenC2 Language Specification that are applicable to PAC. Table
2.1.2-2 extends the list of common Targets and includes
additional Targets unique to PAC. Targets that are defined in
this profile (see Table 2.1.2-2) are referenced with the `pac`
namespace identifier.

#### Table 2.1.2-1 Common Targets Applicable to PAC


#### Table 2.1.2-2 Targets Unique to PAC

Usage Requirements: TBD

### 2.1.3 Command Arguments

Arguments provide additional precision to a Command by including
information such as how, when, or where a Command is to be
executed. Table 2.1.3-1 lists the Command Arguments defined in
Version 1.0 of the OpenC2 Language Specification as they relate
to PAC functionality. Table 2.1.3-2 lists the Command Arguments
that are defined in this profile. Command Arguments that are
defined in this profile (see Table 2.1.3-2) are referenced with
the pac namespace identifier.


#### Table 2.1.3-1 Common Command Arguments Applicable to PAC

#### Table 2.1.3-2 Command Arguments Unique to PAC


Usage Requirements: TBD

#### 2.1.3.1 Data Type Definitions

**Type:** [add type, if necessary]

### 2.1.4 Actuators

An Actuator is the entity that provides the functionality and
performs the Action. The Actuator executes the Action on the
Target. In the context of this profile, the Actuator is the
posture attribute collection. Table 2.1.4-1 lists the PAC
Actuator. 

#### Table 2.1.4-1 PAC Actuator


### 2.1.5 Actuator Specifiers

The presence of one or more Specifiers further refine which
Actuator(s) shall execute the Action. Table 2.1.5-1 lists the
Specifiers that are applicable to the PAC Actuator . Appendix E
provides sample Commands with the use of Specifiers. The Actuator
Specifiers defined in this profile are referenced with the `pac`
namespace identifier.

#### Table 2.1.5-1 PAC Actuator Specifiers




## 2.2 OpenC2 Response Components

Response messages originate from the Actuator as a result of a
Command. Responses associated with required Actions MUST be
implemented. Implementations that include optional Actions MUST
implement the RESPONSE associated with the implemented Action.
Additional details regarding Command and associated Response are
captured in [Section 2.3](#23-openc2-commands). Examples are
provided in [Appendix
F](#appendix-f-example-appendix-with-subsections).


### 2.2.1 Common Response Results

Table 2.2.1-1 lists the Response Results properties defined in
Version 1.0 of the OpenC2 Language Specification that are
applicable to PAC. 

#### Table 2.2.1-1 Common Response Results Applicable to PAC


#### Table 2.2.1-2 Response Results Unique to PAC 

The list of common Response properties is extended to include the
additional Response properties defined in this section and
referenced with the `pac` namespace. 

#### 2.2.1.1 Data Type Definitions

---- OS-Version Table Goes Here -----

Usage Requirements: TBD

---- OS-Arch Table Goes Here -----

Usage Requirements: TBD



### 2.2.2 Response Status Codes

Table 2.2.2-1 lists the Response Status Codes defined in Version
1.0 of the OpenC2 Language Specification that are applicable to
PAC.

#### Table 2.2.2-1 Response Status Codes



## 2.3 OpenC2 Commands

An OpenC2 Command consists of an Action/Target pair and
associated Specifiers and Arguments. This section enumerates the
Commands permitted by this Actuator profile and presents the
associated Response behavior. Sections 2.3.1 through 2.3.5
provide details applicable to each Command, also as influenced by
the Arguments. Table 2.3-1 defines the Commands that are valid in
the context of the PAC profile. An Action (the top row in Table
2.3-1) paired with a Target (the first column in Table 2.3-1)
defines a valid Command.
 
#### Table 2.3-1. Command Matrix

Table 2.3-2 defines the Command Arguments that are allowed for a
particular Command by the PAC Actuator profile. A Command (the
top row in Table 2.3-2) paired with an Argument (the first column
in Table 2.3-2) defines an allowable combination.
 
#### Table 2.3-2. Command Arguments Matrix


Hereafter the specification provides details applicable to each
Command, also as influenced by the Arguments.

### 2.3.1 Scan

Table 2.3-2, Command Arguments Matrix, summarizes the Command
Arguments that apply to all Commands consisting of the scan
Action and a valid Target type.

Upon receipt of a `scan target` Command with an Argument that
is not supported by the Actuator, PAC Consumers:

-   MUST NOT respond with the 200 status code.
-   SHOULD respond with the 501 status code.
-   SHOULD respond with "Argument not supported" in the status
    text.
-   MAY respond with the 500 status code.

OpenC2 Consumers that receive `scan target` Commands:

-   SHOULD respond with the Response status code 200 upon
    successful  parsing of the `scan target` Command and subsequent  implementation of the corresponding rule.

OpenC2 Consumers that receive and successfully parse `scan
target` Commands, but cannot implement the `scan target`:

-   MUST NOT respond with the 200 status code.
-   SHOULD respond with the 501 status code.
-   SHOULD respond with 'Rule not implemented' in the status
    text.
-   MAY respond with the 500 status code.

The valid Target types, associated Specifiers, and Arguments are
summarized in the following subsections. Sample Commands are
presented in [Appendix F](#appendix-f-example-appendix-with-subsections).


#### 2.3.1.1 'Scan Device'

The `scan device` Command is OPTIONAL for Openc2 Producers
implementing the PAC profile. The `scan device` Command is
OPTIONAL for Openc2 Consumers implementing the PAC profile.

The Command does systematic examination of some aspect of the
specified device that implemented the PAC profile.

Products that receive but do not implement the `scan device`
Command:

-   MUST NOT respond with the 200 status code.
-   SHOULD respond with the 501 Response code.
-   SHOULD respond with 'Target type not supported' in the status
    text.
-   MAY respond with the 500 status code.

OpenC2 Consumers that receive and support `scan device` Command:

-   SHOULD respond with the Response status code 200 upon
    successful parsing and execution of the Command.



#### 2.3.1.2 'Scan domain_name'

The `scan domain_name` Command is OPTIONAL for Openc2 Producers
implementing the PAC profile. The `scan domain_name` Command is
OPTIONAL for Openc2 Consumers implementing the PAC profile.

The Command does systematic examination of the specified network
domain name of the devices that implemented the PAC profile.

Products that receive but do not implement the `scan domain_name`
Command:

-   MUST NOT respond with the 200 status code.
-   SHOULD respond with the 501 Response code.
-   SHOULD respond with 'Target type not supported' in the status
    text.
-   MAY respond with the 500 status code.

OpenC2 Consumers that receive and support `scan domain_name`
Command:

-   SHOULD respond with the Response status code 200 upon
    successful parsing and execution of the Command.


#### 2.3.1.3 'Scan mac_addr'

The `scan mac_addr` Command is OPTIONAL for Openc2 Producers
implementing the PAC profile. The `scan mac_addr` Command is
OPTIONAL for Openc2 Consumers implementing the PAC profile.

The Command does systematic examination of the specified MAC
addresses of the devices that implemented the PAC profile.

Products that receive but do not implement the `scan mac_addr`
Command:

-   MUST NOT respond with the 200 status code.
-   SHOULD respond with the 501 Response code.
-   SHOULD respond with 'Target type not supported' in the status
    text.
-   MAY respond with the 500 status code.

OpenC2 Consumers that receive and support `scan mac_addr`
Command:

-   SHOULD respond with the Response status code 200 upon
    successful parsing and execution of the Command.


### 2.3.2 Query

The valid Target types and Arguments for the query Action are
summarized in Table 2.3-1 Command Matrix and Table 2.3-2 Command
Arguments Matrix. Sample Commands are presented in [Appendix
F](#appendix-f-example-appendix-with-subsections).

Upon receipt of `query [target]` Command with an Argument that is
not supported by the Actuator, PAC Consumers:

-   MUST NOT respond with the 200 status code.
-   SHOULD respond with the 501 status code.
-   SHOULD respond with 'Argument not supported' in the status
    text.
-   MAY respond with the 500 status code.

OpenC2 Consumers that receive and support `query [target]`
Command:

-   SHOULD respond with the Response status code 200 upon
    successful parsing and execution of the Command.


#### 2.3.2.1 'query features'

Implementation of the 'query features' Command is REQUIRED and
MUST be implemented in accordance with Section 4.1,
Implementation of 'query features' Command, of Version 1.0 of the
[OpenC2 Language Specification](#openc2-lang-v1.0).

#### 2.3.2.2 ‘Query pac:os\_version’*

The `query pac:os_version` Command provides a mechanism to
collect the information such as name, version and other operating
system related data according to the provided target specifiers.
Implementation of the `query pac:os_version` Command is OPTIONAL.
Products that choose to implement the `query pac:os_version`
Command MUST implement the pac:os\_version Target type described
in Table 2.1.2-2.

### 2.3.3 Cancel

The `command` Target as defined in Version 1.0 of the [OpenC2
Language Specification](#openc2-lang-v1.0) is the only valid
Target type for the cancel Action. The associated Specifiers, and
Arguments are summarized in [Section 2.3.5.1](#update-file).
Sample Commands are presented in [Appendix
F](#appendix-f-example-appendix-with-subsections).

#### 2.3.3.1 `cancel command`

The `cancel command` Command is OPTIONAL for Openc2 Producers
implementing the PAC profile. The `cancel command` Command is
OPTIONAL for Openc2 Consumers implementing the PAC profile.

The Command invalidates a previously issued Action.

Products that receive but do not implement the `cancel command`
Command:

-   MUST NOT respond with the 200 status code.
-   SHOULD respond with the 501 Response code.
-   SHOULD respond with 'Target type not supported' in the status
    text.
-   MAY respond with the 500 status code.

OpenC2 Consumers that receive and support `cancel command`
Command:

-   SHOULD respond with the Response status code 200 upon
    successful parsing and execution of the Command.

### 2.3.4 Update

The `file` Target as defined in Version 1.0 of the [OpenC2
Language Specification](#openc2-lang-v1.0) is the only valid
Target type for the update Action. The associated Specifiers, and
Arguments are summarized in [Section 2.3.4.1](#update-file).
Sample Commands are presented in [Appendix
F](#appendix-f-example-appendix-with-subsections).

#### 2.3.4.1 `update file`

The `update file` Command is used to replace or update files such
as configuration files, rule sets, etc. Implementation of the
update file Command is OPTIONAL. OpenC2 Consumers that choose to
implement the `update file` Command MUST include all steps that
are required for the update file procedure such as retrieving the
file(s), install the file(s), restart/ reboot the device etc. The
atomic steps that take place are implementation specific.

Table 2.3-2, Command Arguments Matrix, presents the valid
Arguments for the `update file` Command. OpenC2 Producers and
Consumers that choose to implement the `update file` Command MUST
NOT include Arguments other than the one identified in Table
2.3-2.

OpenC2 Producers that send the `update file` Command:

-   MAY populate the arguments field with the `response_requested`
    Argument. Valid values for `response_requested` for `update
    file` are "complete", "ack", and "none".
-   MUST NOT include other Command Arguments.
-   MUST populate the name Specifier in the Target.
-   SHOULD populate the path Specifier in the Target.

Upon receipt of an `update file` Command with an Argument that is
not supported by the Actuator, PAC Consumers:

-   MUST NOT respond with the 200 status code.
-   SHOULD respond with the 501 status code.
-   SHOULD respond with 'Argument not supported' in the status
    text.
-   MAY respond with the 500 status code.

OpenC2 Consumers that receive and support the `update file`
Command:

-   upon successful parsing and initiating the processing of the
    'update file' Command, OpenC2 Consumers MAY respond with
    Response status code 102.

-   upon completion of all the steps necessary to complete the
    update and the Actuator commences operations functioning with
    the new file, OpenC2 Consumers SHOULD respond with Response
    status code 200.

-   but cannot parse or process the `update file` Command:

    -   MUST NOT respond with the 200 status code.
    -   SHOULD respond with the 400 status code.
    -   MAY respond with the 500 status code.

-   but do not support the `update file` Command:

    -   MUST NOT respond with the 200 status code.
    -   SHOULD respond with the 501 status code.
    -   SHOULD respond with 'Command not supported' in the status
        text.
    -   MAY respond with the 500 status code.

-   but cannot access the file specified in the file Target:

    -   MUST respond with the 500 status code.
    -   SHOULD respond with 'Cannot access file' in the status
        text.


### 2.3.5 Copy

The `file` Target as defined in Version 1.0 of the [OpenC2
Language Specification](#openc2-lang-v1.0) is the only valid
Target type for the copy Action. The associated Specifiers, and
Arguments are summarized in [Section 2.3.5.1](#update-file).
Sample Commands are presented in [Appendix
F](#appendix-f-example-appendix-with-subsections).

#### 2.3.5.1 `copy file`

The `copy file` Command is used to copy files such as
configuration files, rule sets, etc. Implementation of the copy
file Command is OPTIONAL. OpenC2 Consumers that choose to
implement the `copy file` Command MUST include all steps that are
required for the copy file procedure, such as parse a device and
extract the file based on its name, or/and path, or/and hash
code. The atomic steps that take place are implementation
specific.

Table 2.3-2, Command Arguments Matrix, presents the valid
Arguments for the `copy file` Command. OpenC2 Producers and
Consumers that choose to implement the `copy file` Command MUST
NOT include Arguments other than the one identified in Table
2.3-2.

OpenC2 Producers that send the `copy file` Command:

-   MAY populate the arguments field with the
    `response_requested` Argument. Valid values for
    `response_requested` for `copy file` are "complete", "ack",
    and "none".
-   MUST NOT include other Command Arguments.
-   MUST populate the name Specifier in the Target.
-   SHOULD populate the path Specifier in the Target.

Upon receipt of an `copy file` Command with an Argument that is
not supported by the Actuator, PAC Consumers:

-   MUST NOT respond with the 200 status code.
-   SHOULD respond with the 501 status code.
-   SHOULD respond with 'Argument not supported' in the status
    text.
-   MAY respond with the 500 status code.

OpenC2 Consumers that receive the `copy file` Command:

-   upon successful parsing and initiating the processing of the
    'copy file' Command, OpenC2 Consumers MAY respond with
    Response status code 102.

-   upon completion of all the steps necessary to complete the
    copy of the file, OpenC2 Consumers SHOULD respond with
    Response status code 200.

-   but cannot parse or process the `copy file` Command:

    -   MUST NOT respond with the 200 status code.
    -   SHOULD respond with the 400 status code.
    -   MAY respond with the 500 status code.

-   but do not support the `copy file` Command:

    -   MUST NOT respond with the 200 status code.
    -   SHOULD respond with the 501 status code.
    -   SHOULD respond with "Command not supported" in the status text.
    -   MAY respond with the 500 status code.

-   but cannot access the file specified in the `file` Target:

    -   MUST respond with the 500 status code.
    -   SHOULD respond with "Cannot access file" in the status text.





-------

# 3 Conformance
<!-- Required section -->

> (Note: The [OASIS TC
Process](https://www.oasis-open.org/policies-guidelines/tc-process-2017-05-26/#wpComponentsConfClause)
requires that a specification approved by the TC at the Committee
Specification Public Review Draft, Committee Specification or
OASIS Standard level must include a separate section, listing a
set of numbered conformance clauses, to which any implementation
of the specification must adhere in order to claim conformance to
the specification (or any optional portion thereof). This is done
by listing the conformance clauses here. For the definition of
"conformance clause," see [OASIS Defined
Terms](https://www.oasis-open.org/policies-guidelines/oasis-defined-terms-2018-05-22/#dConformanceClause).

> See "Guidelines to Writing Conformance Clauses":  
https://docs.oasis-open.org/templates/TCHandbook/ConformanceGuidelines.html.

> Remove this note before submitting for publication.)

*This section is normative*.

This section identifies the requirements for twenty-two
conformance profiles as they pertain to two conformance targets.
The two conformance targets are OpenC2 Producers and OpenC2
Consumers.

3.1 Clauses Pertaining to the OpenC2 Producer Conformance Target
----------------------------------------------------------------

All OpenC2 Producers that are conformant to this specification
MUST satisfy Conformance Clause 1 and MAY satisfy one or more of
Conformance Clauses 2 through TBD.

### 3.1.1 Conformance Clause 1: Baseline OpenC2 Producer

An OpenC2 Producer satisfies Baseline OpenC2 Producer conformance
if:

-   3.1.1.1 **MUST** support JSON serialization of OpenC2
    Commands that are syntactically valid in accordance with the
    property tables presented in [Section
    2.1](#21-openc2-command-components).

-   3.1.1.2 All serializations **MUST** be implemented in a
    manner such that the serialization validates against and
    provides a one-to-one mapping to the property tables in
    [Section 2.1](#21-openc2-command-components) of this
    specification.

-   3.1.1.3 **MUST** support the use of a Transfer Specification
    that is capable of delivering authenticated, ordered,
    lossless and uniquely identified OpenC2 messages.

-   3.1.1.4 **SHOULD** support the use of one or more published
    OpenC2 Transfer Specifications which identify underlying
    transport protocols such that an authenticated, ordered,
    lossless, delivery of uniquely identified OpenC2 messages is
    provided.

-   3.1.1.5 **MUST** be conformant with Version 1.0 of the OpenC2
    Language Specification.

-   3.1.1.6 **MUST** implement the `query features` Command in
    accordance with the normative text provided in Version 1.0 of
    the OpenC2 Language Specification.

-   3.1.1.7 **MUST** implement the `response_requested` Command
    Argument as a valid option for any Command.

-   3.1.1.8 **MUST** conform to at least one of the following
    conformance clauses in this specification:

    -   [add Conformance Clause(s), if necessary]

3.2 Clauses Pertaining to the OpenC2 Consumer Conformance Target
----------------------------------------------------------------

All OpenC2 Consumers that are conformant to this specification
MUST satisfy Conformance Clause 19 and MAY satisfy one or more of
Conformance Clauses 20 through 36.

### 3.2.1 Conformance Clause 19: Baseline OpenC2 Consumer

An OpenC2 Consumer satisfies Baseline OpenC2 Consumer conformance
if:

-   3.2.1.1 **MUST** support JSON serialization of OpenC2
    Commands that are syntactically valid in accordance with the property
    > tables presented in [Section 2.1](#21-openc2-command-components) .

-   3.2.1.2 All serializations **MUST** be implemented in a
    manner such that the serialization validates against and provides a one-to-one mapping to the property tables in [Section 2.1](#21-openc2-command-components) of this specification.

-   3.2.1.3 **MUST** support the use of a Transfer Specification
    that is capable of delivering authenticated, ordered, lossless and uniquely identified OpenC2 messages.

-   3.2.1.4 **SHOULD** support the use of one or more published
    OpenC2 Transfer Specifications which identify underlying transport protocols such that an authenticated, ordered, lossless, delivery of uniquely identified OpenC2 messages is provided.

-   3.2.1.5 **MUST** be conformant with Version 1.0 of the OpenC2 Language Specification.

-   3.2.1.6 **MUST** implement the 'query features' Command in accordance with the normative text provided in Version 1.0 of the OpenC2 Language Specification.

-   3.2.1.7 **MUST** implement the `response_requested` Command Argument as a valid option for any Command.

    -   3.2.1.7.1 All Commands received with a
        `response_requested` argument set to 'none' **MUST** process the Command and **MUST NOT** send a Response. This criteria supersedes all other normative text as it pertains to Responses.

    -   3.2.1.7.2 All Commands received without the `response_requested` argument **MUST** process the Command and Response in a manner that is consistent with `"response_requested":"complete"`.

-   3.2.1.8 **MUST** conform to at least one of the following conformance clauses in this specification:

    -   [add Conformance Clause(s), if necessary]



-------

# Appendix A. References

<!-- Required section -->

This appendix contains the normative and informative references
that are used in this document.

While any hyperlinks included in this appendix were valid at the
time of publication, OASIS cannot guarantee their long-term
validity.

## A.1 Normative References

The following documents are referenced in such a way that some or
all of their content constitutes requirements of this document.

(Reference sources: For references to IETF RFCs, use the approved
citation formats at:  
https://docs.oasis-open.org/templates/ietf-rfc-list/ietf-rfc-list.html.  
For references to W3C Recommendations, use the approved citation
formats at:  
https://docs.oasis-open.org/templates/w3c-recommendations-list/w3c-recommendations-list.html.  
Remove this note before submitting for publication.)

###### [OpenC2-Lang-v1.0]
_Open Command and Control (OpenC2) Language Specification Version
1.0_. Edited by Jason Romano and Duncan Sparrell. Latest stage:
https://docs.oasis-open.org/openc2/oc2ls/v1.0/oc2ls-v1.0.html
<!--
###### [OpenC2-HTTPS-v1.0]
_Specification for Transfer of OpenC2 Messages via HTTPS Version 1.0_. Edited by David Lemire. Latest stage: http://docs.oasis-open.org/openc2/open-impl-https/v1.0/open-impl-https-v1.0.html
###### [OpenC2-SLPF-v1.0]
_Open Command and Control (OpenC2) Profile for Stateless Packet Filtering Version 1.0_. Edited by Joe Brule, Duncan Sparrell, and Alex Everett. Latest stage: http://docs.oasis-open.org/openc2/oc2slpf/v1.0/oc2slpf-v1.0.html
-->
###### [RFC2119]
Bradner, S., "Key words for use in RFCs to Indicate Requirement
Levels", BCP 14, RFC 2119, DOI 10.17487/RFC2119, March 1997,
http://www.rfc-editor.org/info/rfc2119.
###### [RFC8174]
Leiba, B., "Ambiguity of Uppercase vs Lowercase in RFC 2119 Key
Words", BCP 14, RFC 8174, DOI 10.17487/RFC8174, May 2017,
http://www.rfc-editor.org/info/rfc8174.

## A.2 Informative References

###### [RFC3552]
Rescorla, E. and B. Korver, "Guidelines for Writing RFC Text on
Security Considerations", BCP 72, RFC 3552, DOI 10.17487/RFC3552,
July 2003, https://www.rfc-editor.org/info/rfc3552.

-------

# Appendix B. Safety, Security and Privacy Considerations

<!-- Optional section -->

(Note: OASIS strongly recommends that Technical Committees
consider issues that might affect safety, security, privacy,
and/or data protection in implementations of their specification
and document them for implementers and adopters. For some
purposes, you may find it required, e.g. if you apply for IANA
registration.

While it may not be immediately obvious how your specification
might make systems vulnerable to attack, most specifications,
because they involve communications between systems, message
formats, or system settings, open potential channels for exploit.
For example, IETF [[RFC3552](#rfc3552)] lists “eavesdropping,
replay, message insertion, deletion, modification, and
man-in-the-middle” as well as potential denial of service attacks
as threats that must be considered and, if appropriate, addressed
in IETF RFCs.

In addition to considering and describing foreseeable risks, this
section should include guidance on how implementers and adopters
can protect against these risks.

We encourage editors and TC members concerned with this subject
to read _Guidelines for Writing RFC Text on Security
Considerations_, IETF [[RFC3552](#rfc3552)], for more
information.

Remove this note before submitting for publication.)

-------

# Appendix C. Acknowledgments

<!-- Required section -->

Note: A Work Product approved by the TC must include a list of
people who participated in the development of the Work Product.
This is generally done by collecting the list of names in this
appendix. This list shall be initially compiled by the Chair, and
any Member of the TC may add or remove their names from the list
by request. Remove this note before submitting for publication.

## C.1 Special Thanks

<!-- This is an optional subsection to call out contributions from TC members. If a TC wants to thank non-TC members then they should avoid using the term "contribution" and instead thank them for their "expertise" or "assistance". -->

Substantial contributions to this document from the following
individuals are gratefully acknowledged:

Participant Name, Affiliation or "Individual Member"

## C.2 Participants

<!-- A TC can determine who they list here, however, TC Observers must not be listed. It is common practice for TCs to list everyone that was part of the TC during the creation of the document, but this is ultimately a TC decision on who they want to list and not list. -->

The following individuals have participated in the creation of
this specification and are gratefully acknowledged:

**OpenC2 TC Members:**

| First Name | Last Name | Company |
| :--- | :--- | :--- |
Philippe | Alman | Something Networks
Alex | Amirnovman | Company B
Kris | Anderman | Mini Micro
Darren | Anstman | Big Networks

-------

# Appendix D. Revision History

<!-- Optional section -->

| Revision | Date | Editor | Changes Made |
| :--- | :--- | :--- | :--- |
| specname-v1.0-wd01 | yyyy-mm-dd | Editor Name | Initial working draft |

-------

# Appendix E. Orchestrator Consumer Operating Model

This appendix explains the operating model for an Orchestrator
Consumer (OC). Figure E-1 shows the relevant operating context.

![Figure E-1: Orchestrator Consumers Context](images/Orchestrator-Consumer.drawio.png)

The diagram illustrates the interactions of the OC with the
upstream Producer that commands it and the downstream Consumers
that it commands. Any particular downstream Consumer may support
any mixture of OpenC2 actuator profiles (APs) and other
non-OpenC2-based interfaces for interacting with the OC. Tracking
the available downstream Consumers and their capabilities is a
local matter for the OC.

## E.1. Terminology

-   **Upstream:** refers to interfaces and external entities
    through which the OC receives OpenC2 commands and via which
    it sends responses.
-   **Downstream:** refers to interfaces and external entities
    through which the OC sends commands via OpenC2 and/or other
    mechanisms and via which it receives responses and data.
-   **OpenC2-based Interfaces:** refers to any interface, inbound
    or outbound, where the OC exchanges information via formats
    and protocols defined by OpenC2 specifications (i.e., OpenC2
    Language Specification, Actuator Profiles, and Transfer
    Specifications).
-   **Other mechanisms:** refers to any interface, inbound or
    outbound, where the OC exchanges information using formats
    and protocols not defined by any OpenC2 specification.


## E.2 Assumptions

1.  All commands received via the OC’s upstream interface:

    1.  Are governed by OpenC2 specifications;

    2.  Are defined by an Actuator Profile not used with any of
        the downstream Consumers (in the figure above this is the
        Posture Attribute Collection (PAC) AP);

    3.  Provide enough information for the OC to select a
        mechanism to interact with downstream Consumers;

    4.  Provide enough information for the OC to determine which
        downstream Consumers to command; the number of downstream
        Consumers can range from a single Consumer to very large
        quantities.

2.  Interactions between the OC and its downstream Consumers may
    use any mixture of OpenC2-based and other mechanisms; the
    mechanisms used are opaque to the upstream Producer.

3.  Responses via the upstream interface will typically only
    provide status information regarding the execution of the
    referenced command, but may contain other requested content
    such as a pointer to stored information, or the actual
    information retrieved, based on specifics of the command
    received from upstream.

Assumption 1.ii is a simplifying assumption: when only the OC
supports the AP defining commands received from upstream, there
is no ambiguity regarding what element executes the command. If
both the OC and downstream Consumers support the AP or LS feature
defining the command received from upstream, the OC must
implement suitable decision logic to determine whether to execute
the command locally or trigger downstream commands derived from
the upstream command.

Assumption 3 alters an OpenC2 Language Specification (LS)
default: [*Section
3.3.1.4*](https://docs.oasis-open.org/openc2/oc2ls/v1.0/cs02/oc2ls-v1.0-cs02.html#3314-command-arguments)
of the LS states that if the command argument `response_requested`
is not explicitly specified by a Producer, then the Consumer
should send a complete response. In the case of an OC responding
to an upstream Producer, this default is overridden.

## E.3 Operations

The OC performs the following operations in executing a command
received from the upstream Producer:

1.  Receive command and validate it against the appropriate AP.

2.  Interpret the received command contents to determine:

    1.  The appropriate mechanism (e.g., OpenC2 AP / command,
        other mechanism) to use with downstream Consumers to
        accomplish the intent of the received command. This
        guides the creation of a derived command to send
        downstream;

    2.  What set of downstream Consumers should receive the
        derived command;

    3.  How to process responses from the downstream Consumers;

    4.  What information must be collected to generate a response
        to the upstream Producer.

3.  Generate and send commands (as identified in 2.a) to the
    identified set of downstream Consumers (as identified in
    2.b).

4.  Process received downstream Consumer responses (as determined
    in 2.c) and accumulate information to generate the response
    to the upstream Producer (as determined in 2.d).

5.  When appropriate, generate and send the response to the
    upstream Producer.


## E.4 Notional Example

The OC receives a command for software bill of material (SBOM)
retrievals from the upstream Producer:

1.  Evaluate the command and determine that it is a valid command
    under the PAC AP.

2.  Interpret the command:

    1.  Identify that the command directs SBOM retrieval, so an
        OpenC2 command conforming to the SBOM AP will be sent to
        downstream consumers

    2.  The actuator specifiers in the received command identify
        a set of downstream consumers by a network address block.
        The OC uses its consumer registration information store
        to identify the specific downstream Consumers
        corresponding to the specified network addresses (for
        this example: 10 downstream Consumers).

    3.  The received command directs that retrieved SBOMs be
        stored in a data store.

    4.  The received command indicates a requested response
        containing a success percentage, and a pointer to the
        stored set of SBOMs from the specified downstream
        consumers.

3.  The OC generates and sends commands in accordance with the
    SBOM AP to retrieve SBOMs from the 10 downstream Consumers
    identified in 2.b.

4.  The OC receives responses containing SBOMs from 8 of the 10
    downstream Consumers, and stores those SBOMs in the
    identified data store. The OC receives error responses from
    the other 2 downstream Consumers.

5.  The OC transmits a response to the upstream Producer
    indicating an 80% success rate and providing a pointer to the
    set of 8 SBOMs in the data store.


-------

# Appendix F. Example Appendix with subsections

## F.1 Subsection title

### F.1.1 Sub-subsection

-------

# Appendix G. Notices

<!-- Required section. Do not modify. -->

Copyright © OASIS Open 2022. All Rights Reserved.

All capitalized terms in the following text have the meanings
assigned to them in the OASIS Intellectual Property Rights Policy
(the "OASIS IPR Policy"). The full
[Policy](https://www.oasis-open.org/policies-guidelines/ipr/) may
be found at the OASIS website.

This document and translations of it may be copied and furnished
to others, and derivative works that comment on or otherwise
explain it or assist in its implementation may be prepared,
copied, published, and distributed, in whole or in part, without
restriction of any kind, provided that the above copyright notice
and this section are included on all such copies and derivative
works. However, this document itself may not be modified in any
way, including by removing the copyright notice or references to
OASIS, except as needed for the purpose of developing any
document or deliverable produced by an OASIS Technical Committee
(in which case the rules applicable to copyrights, as set forth
in the OASIS IPR Policy, must be followed) or as required to
translate it into languages other than English.

The limited permissions granted above are perpetual and will not
be revoked by OASIS or its successors or assigns.

This document and the information contained herein is provided on
an "AS IS" basis and OASIS DISCLAIMS ALL WARRANTIES, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO ANY WARRANTY THAT THE USE
OF THE INFORMATION HEREIN WILL NOT INFRINGE ANY OWNERSHIP RIGHTS
OR ANY IMPLIED WARRANTIES OF MERCHANTABILITY OR FITNESS FOR A
PARTICULAR PURPOSE.

As stated in the OASIS IPR Policy, the following three paragraphs
in brackets apply to OASIS Standards Final Deliverable documents
(Committee Specification, Candidate OASIS Standard, OASIS
Standard, or Approved Errata).

\[OASIS requests that any OASIS Party or any other party that
believes it has patent claims that would necessarily be infringed
by implementations of this OASIS Standards Final Deliverable, to
notify OASIS TC Administrator and provide an indication of its
willingness to grant patent licenses to such patent claims in a
manner consistent with the IPR Mode of the OASIS Technical
Committee that produced this deliverable.\]

\[OASIS invites any party to contact the OASIS TC Administrator
if it is aware of a claim of ownership of any patent claims that
would necessarily be infringed by implementations of this OASIS
Standards Final Deliverable by a patent holder that is not
willing to provide a license to such patent claims in a manner
consistent with the IPR Mode of the OASIS Technical Committee
that produced this OASIS Standards Final Deliverable. OASIS may
include such claims on its website, but disclaims any obligation
to do so.\]

\[OASIS takes no position regarding the validity or scope of any
intellectual property or other rights that might be claimed to
pertain to the implementation or use of the technology described
in this OASIS Standards Final Deliverable or the extent to which
any license under such rights might or might not be available;
neither does it represent that it has made any effort to identify
any such rights. Information on OASIS' procedures with respect to
rights in any document or deliverable produced by an OASIS
Technical Committee can be found on the OASIS website. Copies of
claims of rights made available for publication and any
assurances of licenses to be made available, or the result of an
attempt made to obtain a general license or permission for the
use of such proprietary rights by implementers or users of this
OASIS Standards Final Deliverable, can be obtained from the OASIS
TC Administrator. OASIS makes no representation that any
information or list of intellectual property rights will at any
time be complete, or that any claims in such list are, in fact,
Essential Claims.\]

The name "OASIS" is a trademark of
[OASIS](https://www.oasis-open.org/), the owner and developer of
this specification, and should be used only to refer to the
organization and its official outputs. OASIS welcomes reference
to, and implementation and use of, specifications, while
reserving the right to enforce its marks against misleading uses.
Please see
https://www.oasis-open.org/policies-guidelines/trademark/ for
above guidance.

------

## 1.3 Some markdown usage examples

**Text.**

Note that text paragraphs in markdown should be separated by a
blank line between them -

Otherwise the separate paragraphs will be joined together when
the HTML is generated. Even if the text appears to be separate
lines in the markdown source.

To avoid having the usual vertical space between paragraphs,  
append two or more space characters (or space-backslash) to the
end of the lines  
which will generate an HTML break tag instead of a new paragraph
tag \
(as demonstrated here).

### 1.3.1 Figures and Captions

FIGURE EXAMPLE: <note caption is best placed ABOVE figure, so a
hyperlink to it will actually display the figure, instead of
rendering the figure off the screen above the caption. The same
placement should be used for table captions>

###### Figure 1 -- Title of Figure
![image-label should be meaningful](images/image_0.png) (this
image is intentionally missing)

###### Figure 2 -- OpenC2 Message Exchange
![message exchange](images/image_1.png)


### 1.3.2 Tables

#### 1.3.2.1 Basic Table
**Table 1-1. Table Label**

| Item | Description |
| :--- | :--- |
| Item 1 | Something<br>(second line) |
| Item 2 | Something |
| Item 3 | Something<br>(second line) |
| Item 4 | text |

#### 1.3.2.2 Table with Three Columns and Some Bold Text
text.

| Title 1 | Title 2 | title 3 |
| :--- | :--- | :--- |
| something | something | something else that is a long string of text that **might** need to wrap around inside the table box and will just continue until the column divider is reached |
| something | something | something |

#### 1.3.2.3 Table with a caption which can be referenced

###### Table 1-5. See reference label construction

| Name | Description |
| :--- | :--- |
| **content** | Message body as specified by content_type and msg_type. |

Here is a reference to the table caption: Please see [Table 1-5
or other meaningful
label](#table-1-5-see-reference-label-construction) 


### 1.3.3 Lists

Bulleted list:
* bullet item 1.
* **Bold** bullet item 2.
* bullet item 3.
* bullet item 4.

Indented or multi-level bullet list - add two spaces per level
before bullet character (* or -):
* main bullet type
  * Example second bullet
    * See third level
      * fourth level

Numbered list:
1. item 1
2. item 2
3. item 3

Left-justified list without bullets or numbers: To list multiple
items without full paragraph breaks between items, add
space-backslash after each item except the last.

### 1.3.4 Reference Label Construction

REFERENCES and ANCHORS
- in markdown source, format the Reference tags as level 6
  headings like: `###### [RFC2119]`
###### [RFC2119]
Bradner, S., "Key words ..."

- reference text has to be on a separate line below the tag

- format cross-references (citations of the references) like:
  `see [[RFC2119](#rfc2119)]`  
"see [[RFC2119](#rfc2119)]"  
(note the outer square brackets in markdown will appear in the
visible HTML text)

- The text in the Reference tag (following ###### ) will become
  an HTML anchor using the following conversion rules:  
  - punctuation marks will be dropped (including "[" )  
  - leading white spaces will be dropped  
  - upper case will be converted to lower  
  - spaces between letters will be converted to a single hyphen

- The same HTML anchor construction rules apply to
  cross-references and to section headings.  
  - Thus, a section heading like "## 1.2 Glossary"  
  - becomes an anchor in HTML like `<a href="#12-glossary">`  
  - referenced in the markdown like: see [Section
    1.2](#12-glossary)  
  - in markdown: `"see [Section 1.2](#12-glossary)"`  
  - similar HTML anchors are also used in constructing the TOC

### 1.3.5 Code Blocks

Text to appear as an indented code block with grey background and
monospace font - use three back-ticks before and after the code
block.

Note the actual backticks will not appear in the HTML format. If
it's necessary to display visible backticks, place a back-slash
before them like: \``` .

```
{   
    "target": {
        "x_kmip_2.0": {
            {"kmip_type": "json"},
            {"operation": "RekeyKeyPair"},
            {"name": "publicWebKey11DEC2017"}
        }
    }
}
```

Text to be highlighted as code can also be surrounded by a single
"backtick" character: `code text`

## 1.4 Page Breaks
Add horizontal rule lines where page breaks are desired in the
PDF - before each major section
- insert the line rules in markdown by inserting 3 or more
  hyphens on a line by themselves:  ---
- place these before each main section in markdown (usually "#" -
  which generates the HTML `<h1>` tag)
