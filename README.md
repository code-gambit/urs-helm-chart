# urs-helm-chart
![Android](https://img.shields.io/badge/Helm-3DDC84?style=for-the-badge&logo=helm&logoColor=white) [![Slack](https://img.shields.io/badge/Slack-4A154B?style=for-the-badge&logo=slack&logoColor=white)](https://join.slack.com/t/codegambit/shared_invite/zt-pe1nuhbk-iPuFm2B1JuMS86od4a4wXQ) [![License](https://img.shields.io/badge/License-APACHE-lightgrey.svg?style=for-the-badge)](https://github.com/code-gambit/urs-helm-chart/blob/master/LICENSE) ![GitHub code size in bytes](https://img.shields.io/github/languages/code-size/code-gambit/urs-helm-chart?style=for-the-badge) <br>
[![GitHub Workflow Status](https://img.shields.io/github/workflow/status/code-gambit/urs-helm-chart/Helm%20Lint?style=for-the-badge)](https://github.com/code-gambit/urs-helm-chart/actions/workflows/helm_lint.yml) ![Yaml](https://img.shields.io/badge/Yaml-0095D5?&style=for-the-badge&logo=Yaml&logoColor=white) [![GitHub last commit](https://img.shields.io/github/last-commit/code-gambit/urs-helm-chart?style=for-the-badge)](https://github.com/code-gambit/urs-helm-chart/commits/)

## Project Description
This is the base helm chart for the URL Shortener application. URL shortener is the simple application which help users to get short url against the long url. It is designed to support the distributed system architecture.  

## Chart Dependency
1. [Bitnami/Cassandra](https://artifacthub.io/packages/helm/bitnami/cassandra)
2. [Bitnami/Zookeeper](https://artifacthub.io/packages/helm/bitnami/zookeeper)

## Development Setup
For building the project we need helm installed on your system. Helm has pretty comprehensive guide on installation and setup and [can be found here](https://helm.sh/docs/intro/install/).

### Using the helm chart
Add the below block of code in your helm `requirements.yaml` file.
```yaml
dependencies:
  - name: url-shortener
    repository: https://code-gambit.github.io/urs-helm-chart/charts
    version: 0.1.0
```

### Parameters
For cassandra and zookeeper paramteters refer below bitnami doc.
* [Cassandra](https://artifacthub.io/packages/helm/bitnami/cassandra)
* [Zookeeper](https://artifacthub.io/packages/helm/bitnami/zookeeper)

#### Common parameter
Name | Description | Default Value
--|--|--
common.image_pull_policy | Image pull policy for all the images | "Always"
common.memory.microservices | Memory allocation for the main services | "512M"

#### Connector main parameter
|Name | Description | Default Value|
|--|--|--|
|connector_main.enabled | Boolean value to disable or enable service | true |
|connector_main.name | String for the service name | "connector-main" |
|connector_main.image | String value for the image | "codegb/urs-connector-main" |
|connector_main.cassandra.keyspace_name | Cassandra keysapce name | "" |
|connector_main.cassandra.contact_point |  Conssandra host name or IP | 0.0.0.0 |
|connector_main.cassandra.port | Cassandra port number for communication | 9042 |
|connector_main.cassandra.username | Cassandra db username | "" |
|connector_main.cassandra.local_datacenter | Name of cassandra datacenter | "" |
|connector_main.secret.name | Name of the secret for vulnerable data  | connector-main-secret |
|connector_main.secret.cassandra_password | Cassandra db password | "password" |

## Contributing
DISCLAIMER: Make sure not to force push untill unavoidable.
1. Fork it
2. Create your feature branch `(git checkout -b my-new-feature)`
3. Commit your changes `(git commit -m 'Add some feature')`
4. Clear the checks and make sure build is successfull
5. Push your branch `(git push origin my-new-feature)`
6. Create a new Pull Request.