### Docker samples

#### S2I Builder Image - Spring Boot for Maven3 (Openshift3)

```
docker push cbelleza/springboot-maven3
oc import-image --from=cbelleza/springboot-maven3 springboot
oc new-app springboot~https://github.com/RedHatWorkshops/spring-sample-app.git --name=bootapp

```


#### Tomcat

- Docker
```
docker run -it -p 8080:8080 -v c:/openshift/tomcat:/opt/apache-tomcat/webapps cbelleza/tomcat
```

- Openshift3
```
oc new-app https://github.com/cbelleza/docker-samples.git --context-dir=tomcat
```
