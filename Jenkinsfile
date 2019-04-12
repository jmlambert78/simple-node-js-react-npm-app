pipeline {
  agent {
    label "jenkins-nodejs"
  }
  environment {
    ORG = 'jmlambert78'
    APP_NAME = 'nodereact'
    CHARTMUSEUM_CREDS = credentials('jenkins-x-chartmuseum')
  }
  stages {
    
    stage('Build Release') {
      when {
        branch 'master'
      }
      steps {
        container('nodejs') {

          // ensure we're not on a detached head
          sh "git checkout master"
          sh "git config --global credential.helper store"
          sh "jx step git credentials"

          // so we can retrieve the version in later steps

          sh "npm install"
        }
      }
    }
  }
  post {
        always {
          cleanWs()
        }
  }
}
