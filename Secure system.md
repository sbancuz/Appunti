---
tags:
  - security
---
The CIA paradigm for information security states three requirements:
- **confidentiality** $\to$ only authorized entities can access
- **integrity** $\to$ information can be modified only by authorized entities
- **availability** $\to$ information must be available to all parties

A **vulnerability** is a function of a system that allows to violate one of the constraints of the CIA paradigm. An **exploit** is a specific way to use one or more vulnerability to accomplish a specific objective that violates the constraints. 

An **asset** identifies what is a valuable for an organization and we can define a **threat** as a potential violation of CIA by a **threat agent**. 
An **attack** is an intentional use of one or more exploit with the objective to compromise a CIA.
### Risk management

A **risk** is a statistical and economical evaluation of the exposure to damage because of the presence of vulnerabilities and threats.
$$
\text{Risk} = \text{Assets }\times \text{Vulnerabilities} \times \text{Threats}
$$
																^^ *independent variable*
Security deals with the reduction of vulnerabilities, either with reducing the assets or patching every hole, and management containment. The main pain point with security is **cost balance**, to what point is it worth to invest in security? We can have different costs:
- Direct $\to$ management, operational, equipment
- Indirect $\to$ less usability, slower performance, less privacy, reduced productivity,...

>[!warning]
>More money invested doesn't mean security! e.g. firewall on default settings

There is also a **trust** component to risk management, some parts of our system we can assume that are trustworthy, but actually we have no proof that they actually are, and reliable to work most of the time. Such trusted components are the BIOS, compilers or the hardware. 