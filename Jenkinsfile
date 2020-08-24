pipeline {
    agent any 
    stages {
        stage('Docker Build') {
            steps {
                echo 'Hello, Docker'
                sh 'docker ps'
            }
        }
        stage('git Test') {
            steps {
                echo 'Hello, JDK'
                sh 'git status'
				sh 'git status'
				sh 'git log'
		                sh 'git remote -v'
				sh 'git push -u origin master'
            }
        }
    }
}
