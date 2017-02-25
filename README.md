# Command Central CI Infrastructure 

This project automates Software AG Infrastructure for Continuous Integration:

* Provision Asset Build Enviornment
* Provision Deployer IS instance

## Requirements

First you must [setup your Command Central server](https://github.com/SoftwareAG/sagdevops-cc-server)
with the following:

* Mirror product repository with the following products
  * Integration server
  * Deployer
  * Test Suite
  * Asset Build Environment
* Mirror fix repository with the latest fixes for the above products
* License key files for the above products

To get started fork this project as you will need to customize it.

Then run git submodule initialization procedure to pull antcc library

```bash
git clone https://github.com/SoftwareAG/sagdevops-ci-infra.git
cd sagdevops-ci-infra
git submodule init
git submodule update
```

Verify that your _antcc_ folder is not empty.


## Quck start

Modify [environments/default/env.properties](environments/default/env.properties) file as needed
to point to your product and fix repositories as the license files:

```
# repositories
release=9.12
repo.product=products-${release}
repo.fix=fixes-${release}

# MUST HAVE a valid license key
is.license.key.alias=0000306067_Integration_Server912-lnxamd64
```

Provision ABE and Deployer into the Command Central installation:

```bash
ant up
```

Open [http://localhost:8094/WmDeployer/](http://localhost:8094/WmDeployer/) and login as Administrator/manage


# Building Docker images for ABE and Deployer

NOTE: not complete!

Run this command to setup default 'CI' environment 

```bash
docker-compose up -d deployer builder
docker-compose run --rm up
```

Open up your Command Central to see two new nodes

* Builder - Asset Build Environment 
* Deployer - Open [http://localhost:8094/WmDeployer/](http://localhost:8094/WmDeployer/) and login as Administrator/manage


______________________
These tools are provided as-is and without warranty or support. They do not constitute part of the Software AG product suite. Users are free to use, fork and modify them, subject to the license agreement. While Software AG welcomes contributions, we cannot guarantee to include every contribution in the master project.
