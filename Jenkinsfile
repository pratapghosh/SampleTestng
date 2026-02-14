pipeline {
    agent {
            label 'docker-agent'
        }

    triggers {
         githubPush()
      }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Test') {
            steps {
                sh 'mvn clean test'
            }
        }

    }

    post {
        always {
            testNG reportFilenamePattern: 'target/surefire-reports/testng-results.xml'
        }
    }
}
