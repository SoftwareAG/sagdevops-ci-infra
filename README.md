# Command Central CI Infrastructure 

This project automates provisioning of Software AG infrastructure for Continuous
integration and deployment/delivery:

* Jenkins OSS CI/CD server as a webapp on Command Central server
* JFrog Artifactory OSS binary repository as webapp on Command Central server
* SAG Asset Build Enviornment
* SAG Deployer with WmTestSuite IS instance
* SAG Designer with Local / Service Development

## Requirements

First you must [setup your Command Central server](https://github.com/SoftwareAG/sagdevops-cc-server)
with the following:

* Mirror product repository with the following products
  * Integration server
  * Deployer
  * Unit Test Framework
  * Asset Build Environment
  * Designer with Service Development
* Mirror fix repository with the latest fixes for the above products
* License key files for Integration Server and Unit Test Framework

To get started fork this project as you will need to customize it.

Then run git submodule initialization procedure to pull antcc library

```bash
git clone https://github.com/SoftwareAG/sagdevops-ci-infra.git
cd sagdevops-ci-infra
git submodule init
git submodule update
```

Verify that your _antcc_ folder is not empty.


## Quick start

Modify [environments/default/env.properties](environments/default/env.properties) file as needed
to point to your product and fix repositories and the license files:

```
# repositories
release=9.12
repo.product=products-${release}
repo.fix=fixes-${release}

# MUST HAVE a valid license keys
is.license.key.alias=0000306067_Integration_Server912-lnxamd64
testsuite.license.key.alias=WmTestSuite912-lnxamd64
```

Provision everything into the Command Central installation

```bash
ant up
```

Open Web UIs:

* [Command Central Web UI](https://localhost:8091/cce/web/#installationOverview:ALL/local/1)
* [Deployer](http://localhost:8094/WmDeployer/) and login as Administrator/manage
* [Artifactory](https://localhost:8091/artifactory/)
* [Jenkins](https://localhost:8091/jenkins/)



______________________
These tools are provided as-is and without warranty or support. They do not constitute part of the Software AG product suite. Users are free to use, fork and modify them, subject to the license agreement. While Software AG welcomes contributions, we cannot guarantee to include every contribution in the master project.
