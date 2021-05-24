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

    stage('Smoke Test') {
      steps {
        bat 'mvn test'
      }
    }

    stage('Send Email') {
      steps {
        emailext(subject: 'Job success', body: 'success', from: 'jadhavrahul10@gmail.com', to: 'jadhavrahul10@gmail.com')
      }
    }

    stage('Sonar') {
      steps {
        bat 'mvn sonar:sonar -Dsonar.login=360c39e3bd4503db2e2574692df8147af2cf681e'
      }
    }
    stage('Upload jar') {
      steps {
        nexusArtifactUploader artifacts: [[artifactId: 'junitmavenexample', classifier: '', file: 'target/junitmavenexample-1.0-SNAPSHOT.jar', type: 'jar']], credentialsId: 'jenkinsNexus', groupId: 'com.mycompany.app', nexusUrl: '10.168.140.149:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'jenkin-nexus-storage', version: '4.0.0'
      }
    }

  }
  environment {
    mvn = 'D:\\apache\\apache-maven-3.8.1\\bin\\mvn.exe'
  }
}
