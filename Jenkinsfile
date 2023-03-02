pipeline {
    agent any 
    parameters {
        string defaultValue: 'main', name: 'BRANCH', trim: true
    }
        
    environment {
        BRANCH_NAME = "${BRANCH}"
    stages{
        stage('BUILD') {
            steps{
                 sh '''
                    sleep 5
                    echo "This is a BUILD stage $BRANCH_NAME "
                '''
            }
        }

        stage('TEST') {
            steps{
                sh '''
                    sleep 6
                    echo "This is a TEST stage"
                '''
            }
        }
        stage ('DEPLOY') {
            steps{
                sh '''
                sleep 5
                echo "This is DEPLOY stage"
                '''
            }
        }
    }
  }
