# Introduction

This document describes rules and recommendations for developing applications using the PL/SQL & SQL Language.

SQL, including PL/SQL, code is fundamentally some of the most important code that Insum writes for our customers and partners. The difference between SQL that performs well and SQL that doesn't can be the difference between a successful system (our customers and partners) and a huge disappointment (Healthcare.gov's rollout for example, not done by Insum...).

## Scope

This document applies to the PL/SQL and SQL language as used within ORACLE databases and tools, which access ORACLE databases.

## Document Conventions

SQALE (Software Quality Assessment based on Lifecycle Expectations) is a method to support the evaluation of a software application source code. It is a generic method, independent of the language and source code analysis tools.

### SQALE characteristics and subcharacteristics

Characteristic | Description and Subcharacteristics
-------------- | ----------------------------------
Changeability  | The capability of the software product to enable a specified modification to be implemented.<ul><li>Architecture related changeability</li><li>Logic related changeability</li><li>Data related changeability</li><ul>
Efficiency | The capability of the software product to provide appropriate performance, relative to the amount of resources used, under stated conditions.<ul><li>Memory use</li><li>Processor use</li><li>Network use</li></ul>
Maintainability | The capability of the software product to be modified. Modifications may include corrections, improvements or adaptation of the software to changes in environment, and in requirements and functional specifications.<ul><li>Understandability</li><li>Readability</li></ul>
Portability | The capability of the software product to be transferred from one environment to another.<ul><li>Compiler related portability</li><li>Hardware related portability</li><li>Language related portability</li><li>OS related portability</li><li>Software related portability</li><li>Time zone related portability.</li></ul>
Reliability | The capability of the software product to maintain a specified level of performance when used under specified conditions.<ul><li>Architecture related reliability</li><li>Data related reliability</li><li>Exception handling</li><li>Fault tolerance</li><li>Instruction related reliability</li><li>Logic related reliability</li><li>Resource related reliability</li><li>Synchronization related reliability</li><li>Unit tests coverage.</li></ul>
Reusability | The capability of the software product to be reused within the development process.<ul><li>Modularity</li><li>Transportability.</li></ul>
Security | The capability of the software product to protect information and data so that unauthorized persons or systems cannot read or modify them and authorized persons or systems are not denied access to them.<ul><li>API abuse</li><li>Errors (e.g. leaving a system in a vulnerable state)</li><li>Input validatation and representation</li><li>Security features.</li></ul>
Testability | The capability of the software product to enable modified software to be validated.<ul><li>Integration level testability</li><li>Unit level testability.</li></ul>

### Severity of the rule

!!! bug "Blocker"
    Will or may result in a bug.

!!! danger "Critical"
    Will have a high/direct impact on the maintenance cost.

!!! warning "Major"
    Will have a medium/potential impact on the maintenance cost.

!!! tip "Minor"
    Will have a low impact on the maintenance cost.

!!! info "Info"
    Very low impact; it is just a remediation cost report.

### Keywords used

Keyword     | Meaning
----------- | -------
Always      | Emphasizes this rule must be enforced.
Never       | Emphasizes this action must not happen.
Avoid       | Emphasizes that the action should be prevented, but some exceptions may exist.
Try         | Emphasizes that the rule should be attempted whenever possible and appropriate.
Example     | Precedes text used to illustrate a rule or a recommendation.
Reason      | Explains the thoughts and purpose behind a rule or a recommendation.
Restriction | Describes the circumstances to be fulfilled to make use of a rule.

### Why are standards important

For a machine executing a program, code formatting is of no importance. However, for the human eye, well-formatted code is much easier to read. Modern tools can help to implement format and coding rules.

Implementing formatting and coding standards has the following advantages for PL/SQL development:

* Well-formatted code is easier to read, analyze and maintain (not only for the author but also for other developers).
* The developers do not have to define their own guidelines - it is already defined.
* The code has a structure that makes it easier to avoid making errors.
* The code is more efficient concerning performance and organization of the whole application.
* The code is more modular and thus easier to use for other applications.

This document only defines possible standards. These standards are not written in stone, but are meant as guidelines. If standards already exist, and they are different from those in this document, it makes no sense to change them unless the existing standards have fundamental flaws that would decrease performance and/or significantly decrease the maintainability of code. Almost every system has a mixture of "code that follows the standards" and "code that doesn't follow the standards". Gental migration over time to follow a good set of reasonable standards will always be much better than giving up because standards were not followed in the past.

Overall, the most important thing when writing good code is that you must be able to defend your work.
