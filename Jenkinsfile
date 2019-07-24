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
                
                      when {
                            not {
                                branch 'master'
                            }
                      }
                      steps {
                            echo 'Hello'
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
                                  image 'python:3.5.1'
                          }
                  }
				  stages {
					stage('build') {
						steps {
								sh 'python --version'
						}
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
