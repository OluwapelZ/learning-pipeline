pipeline {
    agent any
          stages {
              stage('One') {
                  steps {
                      echo 'Hi, this is Pelumi'
                  }
              }

              stage('Two') {
                  steps {
                      input('Do you want to proceed?')
                  }
              }

              stage('Three') {
                  when {
                      not {
                          branch "master"
                      }
                  }
                  steps {
                      echo 'Hello, it\'s not on master branch'
                  }
              }

              stage('Four') {
                  parallel {
                      stage('Unit Test') {
                          steps {
                              echo 'Running unit test...'
                          }
                      }

                      stage('Integration Test') {
                          agent {
                              docker {
                                  reuseNode false
                                  image 'ubuntu'
                              }
                          }
                          steps {
                              echo 'Running the integration test...'
                          }
                      }
                  }
              }
          }
}