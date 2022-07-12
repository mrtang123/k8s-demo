#!/usr/bin/env groovy
def branch = 'master'
def repo = "https://github.com/mrtang123/k8s-demo.git"
podTemplate(label: 'default'){
    node('default') {
        stage ("build") {
          container('default') {
                git repo
                sh "mvn clean package -DskipTests"
                sh "docker build -t demo:v1.0.0 ."
            }
        }
        stage ("deploy") {
            container('default'){
               sh "kubectl apply -f Kubernetes/deployment.yaml -n xianzhi"
               sh "kubectl apply -f Kubernetes/services.yaml -n xianzhi"
            }
        }
    }
}
