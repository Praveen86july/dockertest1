pipeline {
    agent any 
    stages {
        stage('Docker Build') {
            agent { docker ps } 
            steps {
                echo 'Hello, Docker'
                sh 'docker ps'
            }
        }
        stage('git Test') {
            agent { git status } 
            steps {
                echo 'Hello, JDK'
                sh 'git status'
				sh 'git add .'
				sh 'git commit -m "modified changes"'
				sh 'git status'
				sh 'git remote -v'
				sh 'git push origin master'
            }
        }
    }
}
