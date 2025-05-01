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
4. static code analysis, linting java sonarcloud
6. create a dockerfile
7. write a pipeline to create a docker container image from dockerfile
8. test it,trigger unit tests, security scans, mutation tests
9. and upload it to ghcr (easiest or dockerhub)
10. build a server somewhere (maybe digital ocean), install k8s on it, setup a load balancer, dns zone
11. install argocd on the k8s cluster
12. create a second repo for infrastructure, apps and manifests connect it to argocd
13. put external-dns, external-secrets, cert-manager, prom- in the repo
14. write a pipeline to create a k8s deployment and a service
15. deploy the stuff on the k8s cluster
16. create an integration test
17. smoke test: curl health check

do the whole thing again for release
user e2e testd
canary blue green
