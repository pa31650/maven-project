pipeline{
    agent any
    stages{
        stage('Build'){
            steps {
                bat 'mvn clean package'                
            }
            post{
                success{
                    echo 'Now Archiving...'
                    archivArtifacts artifacts: '**.target/*.war'
                }
            }
        }
        stage('Deploy to Staging'){
            steps{
                build job: 'Deploy-to-staging'
            }
        }
    }
}