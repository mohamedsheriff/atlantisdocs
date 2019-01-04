************************
Deployment Configuration
************************

Deployment Architecture Principles 
==================================
a) Goal 1: Truely Multi-tenant
b) Goal 2: High Availability 
c) Goal 3: Truely Elastic & Scale out for Loadbalancing
d) Goal 4: Tenancy level SLA gaurantee 
e) Goal 5: Optimized yet meeting the above goals 

Infrastructure Organization
===========================
a) Common Infrastructure: Shared by all the tenants
    * Proxy, Web & Database Servers (Elastic & PostgressDB)
    * WSO2 API Gatway, IAM Servers
    * Logstash & Kibana Server
    * Atlantis Microservices
b) Common Microservices: Shared All the tenants
    * Atlantis Core Server
    * Atlantis Recommendation Core Server
    * Atalntis Datapipeline Server
    * Atlantis Citizen Server
    * Atlantis Integeration Server (Depricated overtime)
c) Tenant Dedicated Infastructure: Dedicated to the tenant based on Elastic Compute principles i.e. dedicated data processing
    * Atlantis Data Procesing Server (Entity Server)
    * Atlantis Data Pipeline Server (Abstraction + IE)
    * Atlantis Media Server

Deployment Inventory (Non HA)
-----------------------------
* Proxy Server:(Ngnix) -  Route the traffic from outside to inside and inside to inside 
* API Gateway Server (Node, WS02 Publisher, WS02 Store, WS02 API Manager): API Authentication and API Loadbalancing
* Dashboard Server (Ngnix, Node, xStreemFS) -  Ngnix based server to host the Angular files
* Atlantis Core Server: (Node, xStreemFS) - Core API's hosted
* Atlantis Citizen Server: Node)- For Citizens
* Atlantis Integeration Engine: (Tomcat,Node) for User Interface & Middleware
* Atlantis ElasticSearch DB Server: (ElasticSearch 6.3) 
* WS02 DB Server: (PostgressDB 9.5)
* Logstash & Kibana Server (Logstash & Kibana 6.3)
* Atlantis Data Processing Server (Entity Engine) (Kafka, WS02 Stream Processor, Node, Zookeeper, Redis)
* Atlantis Data Pipeline Server (Abstraction Layer + IE) - (Node,Redis,xStreemFS) 
* Atlantis Recommendation Core Server (Training and Predict API (Client API)) (Flask, Python 3.6) 
* Atlantis Recommndation Datapipeline Server: For Opendata Pipeline (??)
* Atlantis Media Server (Kurento) 

Base Operating System
---------------------
OS Version: Ubuntu 16.04.4 LTS
Hardening Rules: 
Infastructure:
a) xStreemFS
b) chef client
c) failto ban

Images: 
a) AMI Images (for BETA)
b) VMWARE Image
c) ISO

