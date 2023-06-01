# Biodata Starter Kit SE Deployment Guide

This guide outlines the procedure to deploy the GDI Starter Kit on a Biodata node (Portuguese GDI node). The deployment was executed on a single Virtual Machine (VM), utilizing Docker containers for deploying services.

## System Requirements
- A Virtual Machine (VM) running CentOS Linux release 7.9.2009.

## Prerequisites
Before initiating the deployment process, some software must be installed. Detailed installation instructions can be found at:
- [Snap Installation Guide on CentOS](https://snapcraft.io/docs/installing-snap-on-centos)
- [Certbot Installation Guide on CentOS](https://certbot.eff.org/instructions?ws=other&os=centosrhel7)

## Repositories Required for Deployment

The deployment utilizes several repositories, each offering different components for the overall system. You'll need to use the following repositories:

1. [Starter Kit Storage and Interfaces](https://github.com/GenomicDataInfrastructure/starter-kit-storage-and-interfaces.git) - This repository provides the required storage components and interfaces for the deployment.

2. [Starter Kit HTSget](https://github.com/GenomicDataInfrastructure/starter-kit-htsget.git) - This repository includes the component for data retrieval.

3. [Starter Kit REMS](https://github.com/GenomicDataInfrastructure/starter-kit-rems.git) - This repository manages access rights to resources for the starter kit.

4. [Starter Kit Containerized Computation](https://github.com/GenomicDataInfrastructure/starter-kit-containerized-computation.git) - This repository provides the components for containerized computation, essential for processing genomic data.

5. [Starter Kit Beacon2 RI API](https://github.com/GenomicDataInfrastructure/starter-kit-beacon2-ri-api.git) - This repository contains the Beacon v2 for the starter kit.


## Deployment Procedure
Follow the steps provided below to successfully deploy the GDI Starter Kit:

### Certificate Generation for Services

All user-facing services operate with TLS encryption for secure communication. We utilize Certbot to create these certificates. These certificates are stored in a Docker volume, which is mounted across all the containers. 

To generate the certificates, run the following command:

sudo certbot certonly --standalone --noninteractive --agree-tos --preferred-challenges http --email jorge.miguel.ferreira.silva@ua.pt -d htsget.gdi.biodata.pt -d login.gdi.biodata.pt -d download.gdi.biodata.pt -d beacon.gdi.biodata.pt -d inbox.gdi.biodata.pt -d rems.gdi.biodata.pt --expand

```bash

sudo certbot certonly --standalone --noninteractive --agree-tos --preferred-challenges http --email [user]@[domain] \
-d htsget.gdi.biodata.pt \
-d login.gdi.biodata.pt \
-d download.gdi.biodata.pt \
-d beacon.gdi.biodata.pt \
-d inbox.gdi.biodata.pt \
-d rems.gdi.biodata.pt \
--expand
```
**Important**: Ensure that port 80 is open on your machine when running the command above.


(Add detailed deployment instructions here)


### Note

Bear in mind, the deployment process can vary based on system specifications and configurations. For any issues or further assistance, please refer to our troubleshooting section.

## Troubleshooting
(Add troubleshooting notes and common issues along with their solutions here)

Note: This guide assumes that you have basic understanding of Virtual Machines, Docker containers, and CentOS. If you are not familiar with these topics, we recommend reviewing relevant resources before proceeding.
