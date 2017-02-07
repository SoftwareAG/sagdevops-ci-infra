# Command Central CI Infrastructure 

This project automates Infrastructure for Continous Integration.

## Requirements

First you must [setup your Command Central server](https://github.com/SoftwareAG/sagdevops-cc-server)
using native setup or Docker based setup. 

This example requires Docker based setup.

Ensure you have the following items available in your Command Central server

* 9.12 product repository with the following products
  * Integration server
  * Deployer
  * Test Suite
  * Asset Build Environment
* Fix repository with the latest fixes for the above products
* License key files for the above products


To get started fork this project as you will need to customize it.

Then run git submodule initialization procedure to pull antcc library

```bash
git submodule init
git submodule update
```

Verify that your _antcc_ folder is not empty.

## Customizing configuration

Modify [environments/default/env.properties](environments/default/env.properties) file as needed:

```
# repositories
release=9.12
repo.product=products-${release}
repo.fix=fixes-${release}

# license key
is.license.key.alias=0000306067_Integration_Server912-lnxamd64
```

Run configuration to setup default 'CI' environment 

```bash
docker-compose run --rm up
```

Open up your Command Central to see two new nodes

* Builder - Asset Build Environment 
* Deployer - Open http://localhost:8094/WmDeployer/ and login as Administrator/manage
