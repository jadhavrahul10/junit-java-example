pipeline {
  agent any
  stages {
    stage('Checkout') {
      environment {
        mvn = 'C:\\Program Files\\Git\\bin\\git.exe'
      }
      steps {
        tool(name: 'maven', type: 'maven3.8.1')
        git(url: 'https://github.com/jadhavrahul10/junit-java-example.git', branch: 'master')
      }
    }

    stage('Clean') {
      steps {
        bat(script: 'mvn clean', label: 'mv')
      }
    }

    stage('Test') {
      parallel {
        stage('Test') {
          steps {
            bat 'mvn test'
          }
        }

        stage('Package') {
          steps {
            bat 'mvn package'
          }
        }

      }
    }

  }
}