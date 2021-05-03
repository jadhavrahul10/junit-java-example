pipeline {
  agent any
  stages {
    stage('Checkout') {
      environment {
        mvn = 'C:\\Program Files\\Git\\bin\\git.exe'
      }
      steps {
        tool(name: 'maven', type: 'mvn')
        git(url: 'https://github.com/jadhavrahul10/junit-java-example.git', branch: 'master')
        tool(name: 'maven', type: 'mvn')
      }
    }

    stage('Clean') {
      steps {
        bat 'mvn clean'
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