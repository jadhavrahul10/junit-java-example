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
        tool 'mvn'
        bat(script: 'mvn clean', label: 'mvn')
      }
    }

    stage('Test') {
      parallel {
        stage('Smoke Test') {
          steps {
            bat 'mvn test'
          }
        }

        stage('Regression test') {
          steps {
            bat 'mvn test'
          }
        }

      }
    }

    stage('Reports') {
      steps {
        junit '**/target/surefire-reports/TEST-*.xml'
      }
    }

  }
  environment {
    mvn = 'D:\\apache\\apache-maven-3.8.1\\bin\\mvn.exe'
  }
}