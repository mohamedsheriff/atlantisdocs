************************
Deployment Configuration
************************

Deployment Architecture Principles 
----------------------------------
a) Goal 1: Truely Multi-tenant
b) Goal 2: High Availability 
c) Goal 3: Truely Elastic & Scale out for Loadbalancing
d) Goal 4: Tenancy level SLA gaurantee 
e) Goal 5: Optimized yet meeting the above goals 

Infrastructure Organization
---------------------------
a) Common Infrastructure: Shared by all the tenants
b) Tenant Dedicated Infastructure: Dedicated to the tenant based on Elastic Compute principles i.e. dedicated data processing

Deployment Inventory (Non HA)
-----------------------------
* Proxy Server (Ngnix): Route the traffic from outside to inside and inside to inside 
* API Gateway Server : API Authentication and API Loadbalancing
* Dashboard Server (Aka Web Server) - Ngnix based server to host the Angular files
* Atlantis Core Services: Node Server. Core API's hosted
* Atlantis Citizen Microservices: For Citizens
* Atlantis Integeration Engine: Tomcat & Node for User Interface & Middleware
* Atlantis ElasticSearch DB Server 
* Postgress WS02 DB Server
* Atlantis Entity Engine (Kafka, Streamprocessor, Entiry API Server)
* Atlantis Recommendation Training Server: Training and Predict API (Client API)
* Atlantis Recommndation Opendata: For Opendata Pipeline 

