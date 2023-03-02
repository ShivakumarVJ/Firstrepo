pipeline {
    agent any 
    parameters {
        string defaultValue: 'main', name: 'BRANCH', trim: true
    }
        
    environment {
        BRANCH_NAME = "${BRANCH}"
    }
    
    stages {
        stage('BUILD') {
            steps{
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                 sh '''
                    sleep 5
                    echo "This is a BUILD stage $BRANCH_NAME "
                    Exit 1
                '''
                }
            }
        }

        stage('TEST') {
            parallel {
                stage('Test on MAC machine') {
            steps{
                sh '''
                    sleep 6
                    echo "This is a TEST stage on MAC Machine"
                '''
            }
        }
           stage('Test on Linux machine') {
            steps{
                sh '''
                    sleep 6
                    echo "This is a TEST stage on Linux Machine"
                '''
            }
        }   
                stage('TEST ON Windows MACHINE') {
                    steps {
                        catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                            sh '''
                                sleep 6
                                echo "This is a TEST on WINDOWS"
                                exit 1
                            '''
                        }    
                    }
                }

                stage('TEST ON CHROME MACHINE') {
                    steps {
                        sh '''
                            sleep 6
                            echo "This is a TEST on CHROME"
                        '''
                    }
                }

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

  post {

        always {
            echo "This will run always"
        }

        success {
            echo "This $JOB_NAME SUCCESS - $BUILD_NUMBER $BUILD_ID $BUILD_DISPLAY_NAME"
        }

        unstable {
            echo "This $JOB_NAME UNSTABLE - $BUILD_NUMBER $BUILD_ID $BUILD_DISPLAY_NAME"
        }

        failure {
            echo "This $JOB_NAME FAILED - $BUILD_NUMBER $BUILD_ID $BUILD_DISPLAY_NAME"
        }

    }
}
