---
layout: layout.pug
navigationTitle:  Release Notes
title: Release Notes
menuWeight: 120
excerpt:
featureMaturity:
enterprise: false
---

## Version 1.0.16-5.5.1-beta 

### Improvements
- Default to 0 ingest nodes.
- Automatic management of gateway settings.
- Upgrade to [dcos-commons 0.30.0](https://github.com/mesosphere/dcos-commons/releases/tag/0.30.0).

### Bug Fixes
- Numerous fixes and enhancements to service reliability.

## Version 1.0.15-5.5.1-beta

### Improvements
- Upgrade to [dcos-commons 0.20.1](https://github.com/mesosphere/dcos-commons/releases/tag/0.20.1)
- Upgrade to Elastic 5.5.1

## Version 1.0.14-5.4.1-beta

### New Features
- Installation in folders is supported
- Use of a CNI network is supported

### Improvements
- Upgrade to [dcos-commons 0.20.0](https://github.com/mesosphere/dcos-commons/releases/tag/0.20.0)
- Upgrade to Elastic 5.5.0
- Default user is now `nobody`
- Allow configuration of scheduler log level
- Kibana's cpu and memory are now configurable

### Bug Fixes
- Stop downloading Statsd zip file twice

## Version 1.0.13-5.4.1-beta

### New Features
- Enabled Elastic framework to work in offline/airgapped cluster (#1091)

### Upgrades
- Upgraded to Elasticsearch and Kibana 5.4.1.
- Upgraded to dcos-commons-0.18.0.
