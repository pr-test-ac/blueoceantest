pipeline {
  agent any
  stages {
    stage('Compile') {
      steps {
        withMaven(maven: 'maven3', jdk: 'jdk11') {
          sh 'mvn compile'
        }

      }
    }

    stage('Test') {
      steps {
        withMaven(jdk: 'jdk11', maven: 'maven3') {
          sh 'mvn test'
        }

      }
    }

    stage('Package') {
      steps {
        withMaven(jdk: 'jdk11', maven: 'maven3') {
          sh 'mvn package'
        }

      }
    }
    stage('Archive Artifact') {
      steps {
        archiveArtifacts 'target/*.jar'
      }
    }
    stage('Publish test result') {
      steps {
        junit 'target/**/*.xml'
      }
    }

  }
}
