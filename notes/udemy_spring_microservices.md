# Spring Microservices - Udemy

<h2> Index </h2>  

- [Links](#links)
- [1. Introduction to Microservices Architecture](#1-introduction-to-microservices-architecture)
- [2. Microservices & Spring](#2-microservices--spring)
- [3. Right sizing Microservices & Identifying boundaries.](#3-right-sizing-microservices--identifying-boundaries)
- [4. Getting started with creation of accounts, loands and cards microservices.](#4-getting-started-with-creation-of-accounts-loands-and-cards-microservices)
- [5. Docker: who to build, deploy, scale our microservices using.](#5-docker-who-to-build-deploy-scale-our-microservices-using)
- [6. Deep Dive on Cloud Native Apps & 12factors.](#6-deep-dive-on-cloud-native-apps--12factors)
- [7. Configurations managements in microservices.](#7-configurations-managements-in-microservices)
- [8. Service discovery & registration.](#8-service-discovery--registration)
- [9. Making microservices resilent.](#9-making-microservices-resilent)
- [10. Handling rounting & cross cutting concerns in microservices.](#10-handling-rounting--cross-cutting-concerns-in-microservices)
- [11. Distributed tracing & log aggregation in microservices.](#11-distributed-tracing--log-aggregation-in-microservices)
- [12. Monitoring microservices metrics & health.](#12-monitoring-microservices-metrics--health)
- [13. Automatic self-healing, scaling, deployments using Kubernetes.](#13-automatic-self-healing-scaling-deployments-using-kubernetes)
- [14. Deploying all microsevices into k8s cluster.](#14-deploying-all-microsevices-into-k8s-cluster)
- [15. Deep Dive on Helm.](#15-deep-dive-on-helm)
- [16. Securing microservices using k8s service.](#16-securing-microservices-using-k8s-service)
- [17. Securing microservices using OAuth2 client credentials grant flow.](#17-securing-microservices-using-oauth2-client-credentials-grant-flow)
- [18. Securing microservices using OAuth2 client Authorization code grant flow.](#18-securing-microservices-using-oauth2-client-authorization-code-grant-flow)
- [19. Introduction to K8s ingress & service Mesh (Istio).](#19-introduction-to-k8s-ingress--service-mesh-istio)
- [20. Thank you & congratulations.](#20-thank-you--congratulations)

## Links

* Course Udemy  
https://www.udemy.com/course/master-microservices-with-spring-docker-kubernetes/  

* Oficial Repo  
https://github.com/eazybytes/microservices-with-spring-sectionwise-code  


## 1. Introduction to Microservices Architecture

https://drive.google.com/file/d/1JXyE1jOX0GEd1WWm5ShxKjkW2XlqBEsM/view?usp=share_link

## 2. Microservices & Spring
https://drive.google.com/file/d/1M7bqXiCUi1OzNvoClEVUEdqlarESYfiv/view?usp=share_link

## 3. Right sizing Microservices & Identifying boundaries.
https://drive.google.com/file/d/1TAwGoKeWqnbb7umSPZyaTHrsJSN16tfK/view?usp=share_link

## 4. Getting started with creation of accounts, loands and cards microservices.
Spring Boot review.

## 5. Docker: who to build, deploy, scale our microservices using.
https://drive.google.com/file/d/1z5gSyhPKgY54PXpMP3Z89nfuDROWhP6t/view?usp=share_link

Using Docker
* Virtual Machines VS Containers
<img src="https://antoniodiaz.github.io/images/microservices/microservices_virtualmachines_vs_containers.png" width="600"/>  

* Docker architecture
<img src="https://antoniodiaz.github.io/images/microservices/intro_docker.png" width="600"/>  

* Command to create docker image:
Create a file named `Dockerfile` (without extension) on root folder
Example:
```dockerfile
  #Start with a base image containing Java runtime
FROM openjdk:17-jdk-slim as build

#Information around who maintains the image
MAINTAINER eazybytes.com

# Add the application's jar to the container
COPY target/accounts-0.0.1-SNAPSHOT.jar accounts-0.0.1-SNAPSHOT.jar

#execute the application
ENTRYPOINT ["java","-jar","/accounts-0.0.1-SNAPSHOT.jar"]
```


## 6. Deep Dive on Cloud Native Apps & 12factors.

## 7. Configurations managements in microservices.

## 8. Service discovery & registration.

## 9. Making microservices resilent.

## 10. Handling rounting & cross cutting concerns in microservices.

## 11. Distributed tracing & log aggregation in microservices.

## 12. Monitoring microservices metrics & health.

## 13. Automatic self-healing, scaling, deployments using Kubernetes.

## 14. Deploying all microsevices into k8s cluster.

## 15. Deep Dive on Helm.

## 16. Securing microservices using k8s service.

## 17. Securing microservices using OAuth2 client credentials grant flow.

## 18. Securing microservices using OAuth2 client Authorization code grant flow.

## 19. Introduction to K8s ingress & service Mesh (Istio).

## 20. Thank you & congratulations.
