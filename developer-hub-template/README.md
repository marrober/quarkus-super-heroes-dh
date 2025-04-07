# Quarkus Web Template

This repository contains the Backstage Template used to create the Kubernetes resources needed to build/deploy a simple quarkus application.

## Developer Hub Setup

### Template edits

Since the template is running in a new cluster it is necessary to update the URLs. 

Update : 
* quay url
* gitlab urls (two)
* cluster url (in a step, so this is easy to miss)

### Add Template to Developer Hub

To add the template in this repository to a Developer Hub instance it is necessary to add a link to a file in the GitLab repo. 

Have a look in the config map described below

project : Backstage
config map : backstage-developer-hub-app-config

Around line 93 there are a number of catalog locations. Find a URL line with the target containing this path : rhdh/redhat-developer-templates. After validating that this file is present in the catalog find that file in the GitLab repo. This file will list a number of target template files in the format shown below :

````
apiVersion: backstage.io/v1alpha1
kind: Location
metadata:
  name: showcase-templates
  description: A collection of Backstage templates for RH Summit
spec:
  type: url
  targets:
    - https://gitlab-gitl...
````

Find the GitHub URL for the template that you wish to add. If it is taken from this repo quarkus-super-heroes-dh / developer-hub-template / template.yaml, then add the line below to the above location target list :

https://github.com/marrober/quarkus-super-heroes-dh/blob/main/developer-hub-template/template.yaml

If you wait a few minutes then the template wil be visible in Developer Hub from the 'Create' menu. This then allows you to launch the template.



