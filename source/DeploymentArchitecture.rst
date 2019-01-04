========================
Deployment Configuration
========================

Deployment Architecture Goals 
*****************************

* **Truely Multi-tenant**
* **High Availability**
* **Truely Elastic & Scale out for Loadbalancing**
* **Tenancy level SLA gaurantee** 
* **Optimized yet meeting the above goals** 


Deployment Inventory (Non HA)
*****************************

.. list-table:: List of Servers (No HA mode)
    :widths: 5 10 20 20
    :header-rows: 1
    :stub-columns: 0

    * - Server Name
      - Tenancy Usage
      - Infrastructure Components
      - Role 
    * - Proxy Server
      - Shared
      - ``(Ngnix)``
      - Route the traffic from outside to inside and inside to inside 
    * - API Gateway Server
      - Shared
      - ``Node`` ``WS02 Publisher`` ``WS02 Store`` ``WS02 API Manager``
      - API Authentication and API Loadbalancing
    * - Atlantis Dashboard Server
      - Shared
      - ``Ngnix`` ``Node`` ``xStreemFS``
      - Web Server hosts Dashboard and Platform Server web applications
    * - Atlantis Core Server
      - Shared
      - ``Node`` ``xStreemFS``
      - Atlantis Core & Dashboard API's
    * - Atlantis Citizen Server
      - Tenant Specific
      - ``Node``
      - All the API's realated to citizen application
    * - Atlantis Integration Server
      - Shared :sup:`change to per tenant`
      - ``Node`` ``Tomcat``
      - Integration engine web application and middleware apis
    * - ElasticSearch DB Server
      - Shared
      - ``ElasticSearch 6.3`` 
      - Atlantis Entity, Metrics, Application Database
    * - WS02 Database Server
      - Shared
      - ``PostgressDB 9.5`` 
      - Database required to store IAM and WS02 metadata
    * - Central Log Monintoring Server
      - Shared
      - ``Logstash 9.5`` ``Kibana 9.5`` 
      - Server to process logs and visualize the log stats and logs 
    * - Atlantis Automation Server (Entity Engine)
      - Tenant
      - ``Kafka`` ``WS02 Stream Processor`` ``Node`` ``Zookeeper`` ``Redis``
      - primary server to process device data & events, SOP processing and primary provider of device (entity) API
    * - Atlantis Datapiple Server (Abstraction Layer + IE 2.0)
      - Shared :sup:`change to per tenant`
      - ``Node`` ``xStreemFS`` ``Redis``
      - Primary Server responsible for all datapiple processing for visualization layer (Datasets) and Injection (Adapters) 
    * - Atlantis Media Server
      - Shared
      - ``Kurento``
      -  Media transcoding server converting RTSP streams to Webrtc streams for plugin-less web viewing of camera live streams
    * - Atlantis Recommendation Core Server
      - Shared (change to per  tenant)
      - ``Flask`` ``Python 3.6`` ``Redis``
      -  Responsible for training and providing recommendation engine API
    * - Atlantis Recommendation Data Pipeline Server
      - Shared :sup:`change to per tenant`
      - .. Attention:: :guilabel:`Please verify`
      -  Responsible for recommendation engine datapipeline


.. Note:: The current version of Integeration engine would be deprecated by Atlantis 2.0 GA


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

