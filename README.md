# CI-CD-from-scratch

## plan
### requirements 
- java app
- building a docker container maybe maven??
- runs on kubernetes
- use github actions as pipeline 
### tests:
- test commits
  - basic function test although not sure how todo that
  - maybe unit tests (but this normally do the devs atleast they should do that, so its integrated in the program code) same not sure what to do here...
  - basic syntax test (same should devs do/or their ide should do thst automatically, but maybe makes sense do do it agaib to make sure its correct)
  - owasp ccv security issues
  - linting, static code tests
  - mutation tests
- integration test of the whole thing At cd..
### actual plan
1. pick a program in a java
2. checkout app to this github repo
3. write a pipeline to do test each commit
   1. static code analysis with sonarcloud
   2. linting
4. create a dockerfile
5. write a pipeline to create a docker container image from dockerfile
   1. trigger unit tests   2. security scans
   3. mutation tests
   4. and upload it to ghcr (easiest or dockerhub)
6.  build a server somewhere (maybe digital ocean)
    1.  install k8s on it
    2.  setup a load balancer
    3.  dns zone
7.  install argocd on the k8s cluster
8.  create a second repo for infrastructure, apps and manifests connect it to argocd
9.  put external-dns, external-secrets, cert-manager, prom- in the repo
10. write a pipeline to create a k8s deployment and a service
11. deploy the stuff on the k8s cluster
12. tests:
    1.  create an integration test
    2.  smoke test: curl health check
    3.  user e2e tests

do the whole thing again for release
  user e2e testd
  canary (5%, 10%, 20% ,100%)
  blue green: One Pipeiline for the new features one for the old


# build the java app:

infos in the Dockerfile come from the pom.xml

this helped here: https://scalabledeveloper.com/posts/building-java-applications-using-maven-and-docker-multi-stage-builds/

```bash
docker buildx build -t mavenapp:latest ./
docker run mavenapp
```

# devcontainer

dotfiles come currently from the github setting
its also possible to define it as a feature

the setup.sh works anyway independent of where it runs as its reading its path from the env!

# Next step: Integrate the build of the Dockerfile in a github workflow

# Next step: implement tests in the github workflow