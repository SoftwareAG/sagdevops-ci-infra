# Command Central CI Infrastructure 

This project automates Infrastructure for Continous Integration.

## Requirements

First you must [setup your Command Central server](https://github.com/SoftwareAG/sagdevops-cc-server)

Ensure you have the following available in your Command Central server

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

## How to apply default configuration

Default configuration includes:

* Reference to the products-9.12 product mirror repository
* Reference to the fixes-9.12 fix mirror repository
* No license keys

If the above repositories are not available in your Command Central, 
edit [environments/default/env.properties](environments/default/env.properties) file as set the following properties

* repo.product=<YOUR_PRODUCT_MIRROR_REPO>
* repo.fix=<YOUR_FIX_MIRROR_REPO>

Run configuration to setup default 'CI' environment 

```bash
ant up
```

Verify successful setup by running tests

```bash
ant test
```
