# cloudbees-days-seattle-demo
This is a demo project for the [Cloudbees Days 2019 Seattle](https://www.cloudbees.com/event/cloudbees-days-seattle) event. This
project demonstrates the following:

* Jenkins running in GKE using the [Kubernetes Plugin](https://github.com/jenkinsci/kubernetes-plugin)

* Utilizing GCP officially supported Jenkins plugins: ([GCS](https://github.com/jenkinsci/google-storage-plugin), [OAuth](https://github.com/jenkinsci/google-oauth-plugin), [GKE](https://github.com/jenkinsci/google-kubernetes-engine-plugin))

* Demonstrates best practices with real world use-case
  * Builds and tests [SpringBoot](https://spring.io/guides/gs/spring-boot/) Application
  * Publishes container image to [GCR](https://cloud.google.com/container-registry/) using [Kaniko](https://github.com/GoogleContainerTools/kaniko)
  * Uses the [Jenkins GKE]((https://github.com/jenkinsci/google-kubernetes-engine-plugin)) plugin to deploy to multiple clusters in [GKE](https://cloud.google.com/kubernetes-engine/)


# Setup steps
The follow describes the setup process for this project.

1. Install Jenkins on GKE using the stable/jenkins helm chart: [Jenkins On GKE Tutorial](https://cloud.google.com/solutions/jenkins-on-kubernetes-engine-tutorial)

1. Install and configure the GKE plugin: [Jenkins GKE Docs](https://github.com/jenkinsci/google-kubernetes-engine-plugin/blob/develop/docs/Home.md)

1. Add GCP SA JSON key to secret store for kaniko:
`kubectl create secret generic kaniko-secret --from-file=<path to kaniko-secret.json>`

1. Create a new Multibranch Pipeline Jenkins project pointed at this repository: [Jenkins Multibranch Pipeline Tutorial](https://jenkins.io/doc/tutorials/build-a-multibranch-pipeline-project/)


