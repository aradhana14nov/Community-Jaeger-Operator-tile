---
title: Jaeger Operator Tutorial to check distributed tracing using Jaeger UI
description: This tutorial explains how to check distributed tracing of services using Jaeger UI
---

### Jaeger UI

Once our microservices are successfully configured for auto-tracing we can check the traces on Jaeger UI.

Follow below steps to check traces on Jaeger UI:

1. On the services dropdown you will see all these services which are deployed on cluster and enabled for autotrace as shown in below snapshot: 

![](_images/service-autotracing-jaeger-ui.PNG)

2. Select "service-a" from drop down. You can select the operations you want to trace using "Operation" drop-down and other drop-down options provided by the UI and click on "Find Traces" button.

operations

3. You can see number of traces produces with the unique trace id as shown in below snapshot.

 see-detailed-trace-of-all-the-services

4. You will see all the three services traces as shown in below snapshot:

services-tracing

5. Also to get more details, you can expand the traces view by clicking on small down arrow option "v" against each services. You will see something similar to below snapshot:

services-expanded-form

You can also see the logs and warning details against each services operations: "Pass" and "Get" which will provide important information while tracing your services.

logging-warning-msg


6. You can compare two traces by selecting the check box corresponding to each trace id and click on "Compare" option as shown in below snapshot a:


compare-services-traces

You will see the flow how these services : service-a,service-b and service-c requests flows using "Compare" option.

compare-services

7. You can view Architecture DAG view using the option "System Architecture" "DAG" option. See below snapshot:

system-architecture


