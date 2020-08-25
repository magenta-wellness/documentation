## User Guide

[On-board a Client](client/on-boarding.md): Steps necessary to on-board a Client.

[System notes](/SYSTEM_NOTES.md)

## Product History
Wellness started out as a side project which needed to be done as soon as possiple and it was made clear that there wasa no need for further development.

Therefore, we created a monolithic app using Symfony and SonataAdminBundle where CRUD machanisms were inspired by Django.

A few months later, there turned out to be some new business development and a great deal of new features had to be implemented regardless the missing of automated tests and proper developer workflow.

Two years later, after a series of big and small updates, the core system became error-prone and some third-party libraries became outdated so the core system was frozen from any new developments and the project was renamed to "legacy".

To understand the "legacy" project, read its [Software Requirement Specification](/software_requirements_spec.md).

After a while, Wellness got a very big partner in Myanmar and they need a reporting app to see the claims made by their employees.

\> A new app was created and transaction data are synced from the core database. This app is a separate symfony app with its own codebase and database.

Check the Symfony project under folder "sym-src" of "legacy" repository to [view its SRS](/software_requirements_spec.md).

