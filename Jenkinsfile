pipeline {
  agent any
  stages {
    stage('Checkout') {
      environment {
        mvn = 'D:\\apache\\apache-maven-3.8.1\\bin\\mvn.exe'
      }
      steps {
        git(url: 'https://github.com/jadhavrahul10/junit-java-example.git', branch: 'master')
      }
    }

    stage('Clean') {
      agent any
      environment {
        mvn = 'D:\\apache\\apache-maven-3.8.1\\bin\\mvn.exe'
      }
      steps {
        bat(script: 'clean', label: 'mvn')
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
  environment {
    mvn = 'D:\\apache\\apache-maven-3.8.1\\bin\\mvn.exe'
  }
}