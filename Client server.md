---
tags:
  - distributed_systems
---
Components have different roles and provide a well defined API to access its services.
#### Tiers

Often servers operate by taking advantage of the services offered by other components. So an application can be partitioned by 3 classes:
- UI
- Application services
- Storage services

>[!warning]
>There can be an infinite amount of tiers, it depends on the needs of the application

![[Ntiers.png]]
