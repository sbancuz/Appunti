---
tags:
  - distributed_systems
---
It's build around the concepts of: 
- services: loosely coupled units of functionality
- service providers: those who export the services
- service consumer: those who use the services with message passing or method invocation
- service brokers: they hold the description of available services to be searched by consumers

![[services oriented.png]]

Typically it works through message passing and method invocations. An important concept is the orchestration of all the services, this is a components that acts as both a provider and a consumer. 
### Web services

These are services designed to support interoperable machine to machine interactions over a network. Their interfaces are described in WSDL and invoked through [[SOAP]] and managed by [[UDDI]]
