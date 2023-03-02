pipeline {
    agent any 
    parameters {
        string defaultValue: 'shivu', description: 'Choose your name', name: 'name'
        
        string defaultValue: 'Hubli', description: 'Choose your location', name: 'location'

    }
        
    stages{
        stage('BUILD') {
            steps{
                 sh '''
                    sleep 5
                    echo "This is a BUILD stage "
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
    }
}
