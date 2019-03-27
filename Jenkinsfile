pipeline {
  agent any
  stages {
    stage('Initialize') {
      steps {
        sh 'bash ./jenkins/scripts/init.sh'
      }
    }
    stage('Restore and Build') {
      steps {
        sh 'bash ./jenkins/scripts/restore-build.sh'
        echo 'Restore and Build Completed Successfully'
      }
    }
    stage('Test') {
      steps {
        sh 'bash ./jenkins/scripts/test.sh'
      }
    }
    stage('Publish') {
      steps {
        sh 'bash ./jenkins/scripts/publish.sh'
        echo 'Publish Successfully Completed ....'
      }
    }
    stage('Prepare Image') {
      steps {
        sh 'bash ./jenkins/scripts/prepare-image.sh'
      }
    }
    stage('Publish Image') {
      steps {
        sh 'bash ./jenkins/scripts/push-image.sh'
      }
    }
  }
  environment {
    CONTAINER_NAME = 'restservicesv2'
    HOME = '.'
  }
}