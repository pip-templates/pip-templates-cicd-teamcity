# Overview

This is template for teamcity pipeline for node js microservice. View dockerfiles in [Dockerization template](https://github.com/pip-templates/pip-templates-microservice-dockerization).

# Usage

Copy component.json, and *.ps1 scripts to microservice folder and manually create build configuration (pipeline) on teamcity. You need to set 
1. Version Control Settings - attach git repository as VCS root
2. Build Steps - create 'Command line' steps and run powershell scripts in next order 
    1) build.ps1
    2) test.ps1
    3) package.ps1
    4) publish.ps1
    5) tag.ps1
    6) release.ps1
    7) clean.ps1

    For clean step set Execution to 'Always, even if build stop command was issued'.
3. Triggers - enable vcs trigger
4. Parameters - set required environment variables.

# Settings

Required environment variables:
* **DOCKER_IP** - docker ip for gitlab runner
* **DOCKER_USER** - docker username to access docker registry on image publish
* **DOCKER_PASS** - docker password to access docker registry on image publish
* **RETRY** - set true to restart pipeline in case of falure on npm install
* **NPM_USER** - credentials required for release script. npm username
* **NPM_PASS** - credentials required for release script. npm password
* **NPM_EMAIL** - credentials required for release script. npm email

Set all of this variables on teamcity build configuration Parameters - Environment variables.
