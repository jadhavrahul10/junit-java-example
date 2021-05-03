pipeline {
  agent any
  stages {
    stage('Checkout') {
      environment {
        mvn = 'D:\\apache\\apache-maven-3.8.1\\'
      }
      steps {
        tool(name: 'mvn', type: 'maven3.8.1')
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
  environment {
    mvn = 'D:\\apache\\apache-maven-3.8.1\\'
  }
}
