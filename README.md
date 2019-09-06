# Red Hat Decision Manager 7 OpenShift images

This repository contain all the image descriptors and files necessary to build the RHPAM images.
It also includes the application templates, however they are deprecated in 7.6. Using the Red Hat Business Automation Operator is recommended.


### Repo structure:
rhdm-7-openshift-image \
├── [controller](controller): RHDM Controller  image descriptor files. \
├── [decisioncentral](decisioncentral): Decision Central image descriptor files. \
├── [kieserver](kieserver): Execution Server image descriptor files. \
├── [optaweb-employee-rostering](optaweb-employee-rostering): Optaweb Employee Rostering image descriptor files. \
├── [quickstarts](quickstarts): quickstarts used as example in some of the application templates. \
└── [templates](templates): Application templates, used to instantiate a new RHDM environment on OpenShift. (Deprecated)  \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── [docs](templates/docs):  Application templates docs generated by the [gen_template_docs.py](https://github.com/jboss-container-images/jboss-kie-modules/blob/master/tools/gen-template-doc/gen_template_docs.py) script.

Inside each image directory you will find the following files:

 - **container.yaml**: used by OSBS builds.
 - **content_sets.yaml**: define the yum repositories needed to install dependencies for the image.
 - **branch-overrides.yaml**: overrides file which uses the latest stable version for external dependencies. The module.yaml and image.yaml always refer to master branch.
 - **tag-overrides.yaml**: Used to override the branchs to use the final tags to rebuild released images, for CVE respins.
 - **image.yaml**: the main image descriptor file, here are all the pieces and configuration needed to build an image.


On the root directory you can also find the two files:
 - [example-app-secret-template.yaml](example-app-secret-template.yaml): Contains a https certificate to be used as example where https is required.
 - [rhdm-image-streams.yaml](rhdm76-image-streams.yaml): imagestreams definitions, file used to install the product image streams on OpenShift, this files contains the image stream name and the registry the image will be pulled of.


This repo depends directly on 5 repositories, which are:
 - [cct_module](https://github.com/jboss-openshift/cct_module.git): contains some core modules, like s2i and maven.
 - [jboss-eap-modules](https://github.com/jboss-container-images/jboss-eap-modules.git): contains modules responsible to configure JBoss EAP, like datasources and the base configuration files.
 - [jboss-eap-image](https://github.com/jboss-container-images/jboss-eap-7-image.git): provides the EAP modules, which is used to install the EAP on the target image.
 - [rhdm-7-image](https://github.com/jboss-container-images/rhdm-7-image.git): provides the RHDM binaries modules.
 - [jboss-kie-modules](https://github.com/jboss-container-images/jboss-kie-modules): contains all the resources used to configure the RHDM images.


##### Found a issue?
Please submit a issue [here](https://issues.jboss.org/projects/RHDM) with the **Cloud** tag or send us a email: bsig-cloud@redhat.com.
