### Docker samples

#### How to run

- Tomcat (Docker)
```
docker run -it -p 8080:8080 -v c:/openshift/tomcat:/opt/apache-tomcat/webapps cbelleza/tomcat
```

- Tomcat (Openshift3)
```
oc new-app https://github.com/cbelleza/docker-samples.git --context-dir=tomcat
```
