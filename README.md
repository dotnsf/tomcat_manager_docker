# Tomcat Manager on Docker


## Overview

How to deploy Apache Tomcat on Docker( with manager app ).


---

## How to deploy

- Edit `username` and `password` in `tomcat-users.xml` in this folder for your use.

- Copy `tomcat-users.xml` and `context.xml` under `/tmp/`.

  - `$ cp ./tomcat-users.xml /tmp`

  - `$ cp ./context.xml /tmp`

- Run Tomcat in Docker

  - `$ docker run --name tomcat -it -p 8080:8080 -v /tmp/tomcat-users.xml:/usr/local/tomcat/conf/tomcat-users.xml -v /tmp/context.xml:/tmp/context.xml tomcat:9.0 /bin/bash -c "mv /usr/local/tomcat/webapps /usr/local/tomcat/webapps2; mv /usr/local/tomcat/webapps.dist /usr/local/tomcat/webapps; cp /tmp/context.xml /usr/local/tomcat/webapps/manager/META-INF/context.xml; catalina.sh run"`

- Access to manager application

  - `http://localhost:8080/manager/html`

  - Use username and password, which are edited in `tomcat-users.xml` above, for Basic Authentication dialog.

- You will see manager application UI there.


---

## References

https://octopus.com/blog/deployable-tomcat-docker-containers


---

## Licensing

This code is licensed under MIT.


---

## Copyright

2022  [K.Kimura @ Juge.Me](https://github.com/dotnsf) all rights reserved.
