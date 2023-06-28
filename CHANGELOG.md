# Changelog

All notable changes to this project will be documented in this file. 

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

-------
## [Unity Release 23.2] - 2023-06-30

### Added 
- Updated implementation and initial release of the [On-Demand CloudFormation templates v0.0.1](https://github.com/unity-sds/unity-on-demand-cloudformation/releases/tag/v0.0.1)
  - port management console instance AMI from Amazon Linux 2 to Ubuntu 20.04 LTS
  - deploy and startup the management console v0.2.9 (unity-sds/unity-on-demand#28)
  - remove deployment of On-Demand REST API, EKS and SPS from CloudFormation (unity-sds/unity-on-demand#26)
    - these will be deployed via the management console
  - apply cost tags to management console instance (unity-sds/unity-cs#213)
- Updated implementation and release of the [On-Demand REST API v0.0.2](https://github.com/unity-sds/unity-on-demand-api/releases/tag/v0.0.2)
  - update the prewarm endpoint to forward requests to the SPS API (unity-sds/unity-on-demand#23)
    - in 23.1 this endpoint bypassed the SPS API and directly manipulated the worker node count via the EKS API
  - implemented capability to trigger pre-warm based on a schedule or data arrival
    - added serverless deployment of an AWS lambda function that triggers a prewarm call to the On-Demand API
      - this single AWS lambda function is used to trigger prewarm based on:
        - on a cron-like schedule using AWS EventBridge (unity-sds/unity-project-management#62)
        - upon data arrival using S3 events (unity-sds/unity-project-management#61)
- Updated documentation
  - Gitbook: https://unity-sds.gitbook.io/docs/developer-docs/on-demand/deployment-of-on-demand-sps
- Video demo of management console deployment via CloudFormation
  - https://drive.google.com/file/d/1kfX1jE_sP1OWiG7kfOeI3FtX2a7Sz4ip/view?usp=drive_link

-------
## [Unity Release 23.1] - 2023-04-07

### Added 

- Initial implementation and release of the On-Demand REST API (v0.0.1)
  - https://github.com/unity-sds/unity-on-demand-api/releases/tag/v0.0.1
- Initial documentation
  - Gitbook: https://unity-sds.gitbook.io/docs/developer-docs/on-demand/docs/user-guide/on-demand-api
  - github.io: https://unity-sds.github.io/unity-on-demand-api/
- Video demo of prewarm capability
  - https://drive.google.com/file/d/1I22iwbLoi8JfdD38-31DF7SB80HFWzik/view?usp=share_link
