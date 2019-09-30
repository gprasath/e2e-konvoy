### NSCD-Verifying application HA consuming jiva volume post application pod kill.

#### Description

This job ensures that the application consuming jiva volume runs seamlessly on inducing the application pod failure.

#### Prerequisites

- D2IQ-Konvoy Cluster should be created and have the dependencies installed.
- Jiva based storage pool should have been created.

#### Procedure

- This job triggers the litmus experiments which induces failure on one of the application pods and ensures that there is no impact.
- The litmus experiment receives the necessary parameters in form of pod environmental variables and updates the manifest files accordingly.
- This job deploys busybox statefulset application consuming OpenEBS Volume and checks if the application is deployed successfully.
- Then it induces application pod kill chaos and verify if the application pod is rescheduled and running successfully.
- Finally, the job deletes the busybox deployment.

#### Expected result

- Application pod should be rescheduled successfully.

#### Test result


| Job ID |   Test Description         | Execution Time |Test Result   |
 |---------|---------------------------| --------------|--------|
 |    <a href="https://gitlab.openebs.ci/openebs/e2e-konvoy/-/jobs/90324">90324</a>   |  Induce application pod failure and check if it is recovered successfully           |  Mon Sep 30 22:26:58 IST 2019     |<a href="https://e2e-logs.openebs100.io/app/kibana#/discover?_g=(refreshInterval:(pause:!t,value:0),time:(from:now-7d,mode:quick,to:now))&_a=(columns:!(_source),filters:!(('$state':(store:appState),meta:(alias:!n,disabled:!f,index:cluster-logs,key:commit_id,negate:!f,params:(query:'038d3ae24ce0c7364f36918c475e07a98fd15ed0',type:phrase),type:phrase,value:'038d3ae24ce0c7364f36918c475e07a98fd15ed0'),query:(match:(commit_id:(query:'038d3ae24ce0c7364f36918c475e07a98fd15ed0',type:phrase)))),('$state':(store:appState),meta:(alias:!n,disabled:!f,index:cluster-logs,key:pipeline_id,negate:!f,params:(query:'3378',type:phrase),type:phrase,value:'3378'),query:(match:(pipeline_id:(query:'3378',type:phrase))))),index:cluster-logs,interval:auto,query:(language:lucene,query:''),sort:!('@timestamp',desc))">Pass</a>  |
