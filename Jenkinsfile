pipeline {
    agent {
        label "jenkins-nodejs"
    }
    stages {
        stage('Build') { 
            steps {
                sh 'npm install' 
            }
        }
    }
}
