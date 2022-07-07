#!/usr/bin/env groovy
def branch = 'master'
def repo = "https://github.com/cvemula1/K8s-Docker-Jenkins-CICD.git"
podTemplate(label: 'default'){
    node('default') {
        stage ("build") {
          container('default') {
                git repo
                sh "mvn clean install"
                sh "docker build -t demo:v1.0.0 ."
            }
        }
        stage ("deploy") {
            container('default'){
               sh "kubectl apply -f Kubernetes/deployment.yaml -n <Kubernetes-NameSpace>"
               sh "kubectl apply -f Kubernetes/services.yaml -n <Kubernetes-NameSpace>"
            }
        }
    }
}
