pipeline {
    agent any 
    environment {
        docker_host = "10.1.0.187"
    }
    stages {
        stage('cloning github repo') {
          steps {
            sh 'rm -rf dockertest1'
            sh 'git clone https://github.com/praveen86july/dockertest1.git'
            }
        }
        stage('build docker image') {
          steps {
            sh 'cd /var/lib/jenkins/workspace/pipeline1/dockertest1'
            sh 'cp /var/lib/jenkins/workspace/pipeline1/dockertest1/* /var/lib/jenkins/workspace/pipeline1'
            sh 'docker build -t praveen86july/pipelinetestprod:${BUILD_NUMBER} .'
            }
        }
        stage('push image to docker hub') {
          steps {
            sh 'docker push praveen86july/pipelinetestprod:${BUILD_NUMBER}'
            }
        }
        stage('deploy to docker host') {
          steps {
            sh 'docker -H tcp://$docker_host:2375 stop prodwebapp1 || true'
            sh 'docker -H tcp://$docker_host:2375 run --rm -dit --name prodweb1 --hostname prodwebapp1 -p 8000:80 praveen86july/pipelinetestprod:${BUILD_NUMBER}'
            }
        }
        stage('check webapp rechability') {
          steps {
            sh 'sleep 10s'
            sh 'curl http://$docker_host:8000'
            }
        }   
    }
}
