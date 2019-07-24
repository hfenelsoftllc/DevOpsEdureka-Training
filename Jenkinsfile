pipeline {
    agent any
    stages {
        stage('One') {
                steps {
                      echo 'Hi, this is my first pipeline in jenkins'
                }
        }
        stage('Two'){
                steps {
                    input('Do you want to proceed?')
                }
        }
        stage('Three'){
                steps{
                      when {
                            not {
                                branch 'master'
                            }
                      }
                      steps {
                            echo 'Hello'
                      }
                }
        }
         stage('Four'){
                parallel {
                  stage('Unit-Test') {
                          steps {
                                echo 'Running the unit test...'
                          }
                  }
                  stage('Integration test') {
                  agent {
                          docker {
                                  reuseNode false
                                  image 'ubuntu'
                          }
                  }
                          steps {
                                  echo 'Running Integration test...'
                          }
                  }
                }
         }
         
         
       
    }
}
