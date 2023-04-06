# Agent Check: Choreo

## Overview

[Choreo][1]  is your SaaS application development suite designed to accelerate the creation of digital experiences. Build, deploy, monitor, and manage your cloud native applications while increasing developer productivity and focusing on innovation.

This integration makes it possible for you to observe [Ballerina][2] components running in Choreo private data planes. The Choreo integration creates a dashboard that can be used to view application metrics, system metrics, and logs related to your Ballerina components. 

## Setup

### Installation

Setting up Datadog observability for your Private Data Plane requires support from the WSO2 team. Please reach out to your WSO2 Account Manager or [contact us here][3] so that the WSO2 team can set up the Datadog agent in the cluster.

Once the Datadog agent has been installed by the WSO2 team, you can install this integration in your Datadog account.


### Configuration

For the Datadog agent to collect metrics from Ballerina components running in Choreo, the pods need to be annotated as follows. Please refer [Autodiscovery Integration Templates][4] for more information.

```yaml
apiVersion: v1
kind: Pod
# (...)
metadata:
  name: '<POD_NAME>'
  annotations:
    ad.datadoghq.com/<CONTAINER_IDENTIFIER>.checks: |
      {
        "choreo": {
          "instances": [{'openmetrics_endpoint':"http://%%host%%:9797/metrics"}]
        }
      }      
    # (...)
spec:
  containers:
    - name: '<CONTAINER_IDENTIFIER>'
# (...)
```

## Data Collected

### Metrics

See [metadata.csv][5] for a list of metrics provided by this check.

### Service Checks

Choreo does not include any service checks.

### Events

Choreo does not include any events.

## Troubleshooting

Need help? Contact [Datadog support][6].

[1]: https://wso2.com/choreo
[2]: https://ballerina.io
[3]: https://wso2.com/contact
[4]: https://docs.datadoghq.com/containers/kubernetes/integrations/?tab=kubernetesadv2 
[5]: https://github.com/DataDog/integrations-extras/blob/master/choreo/metadata.csv
[6]: https://docs.datadoghq.com/help