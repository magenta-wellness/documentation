## User Guide

[On-board a Client](client/on-boarding.md): Steps necessary to on-board a Client.


## Product History
Wellness started out as a side project which needed to be done as soon as possible, and it was made clear that there was no need for further development.

Therefore, we created a monolithic app using Symfony and SonataAdminBundle where CRUD mechanisms were inspired by Django.

A few months later, there turned out to be some new business development, and a number of new features had to be implemented regardless of the missing of automated tests and proper developer workflow.

Two years later, after a series of big and small updates, the core system became error-prone and some third-party libraries became outdated, so the core system was frozen from any new developments. The project was renamed to "legacy".

To understand the "legacy" project, read its [Software Requirements Specification](https://github.com/magenta-wellness/legacy/blob/master/sym-src/insurer/documentation/software_requirements_spec.md).

After a while, Wellness got a very big partner in Myanmar and they need a reporting app to see the claims made by their employees.

\> A new app was created and transaction data were synced from the core database. This app is a separate symfony app with its own codebase and database.

Check the Symfony project under folder "sym-src" of the "legacy" repository to [view its SRS](https://github.com/magenta-wellness/legacy/blob/master/sym-src/insurer/documentation/software_requirements_spec.md).

The reporting module for IKBZ (a big Myanmar client) was supposed to be a one-time project and stop growing functionally.
However, just a few weeks after the delivery of this module, the team get a request to extend this module and add more features to it to allow account manager to view redemption reports and generate invoices plus uploading properties of payment for each invoice.
Hence, the codebase got ugly and also lacked automated tests.

[View SRS](https://github.com/magenta-wellness/app-account-manager/blob/master/documentation/software_requirement_specification.md) of the account manager module to get a more detailed view of the system.

If you have read the legacy SRS, you must have seen the functional requirements for "evoucher". This module was created for white-collar workers to access their products and services.
Blue-collar workers, however, do not have the required skills to have this functionality installed on their phone to properly make good use of it.
For that reason, compares with many blue-collar workers needed to use a Wellness Medical Chit to full in the worker's details and give it to them to redeem at the clinic.
This, however, has caused a huge problem in managing and entering those chits into the system.
Therefore, a new service called Digital Medical Chit was created and deployed separately to eliminate the need for a physical Medical Chit.

[System notes](https://github.com/magenta-wellness/legacy/blob/master/sym-src/insurer/documentation/system_notes.md)