pipeline {
    agent any
    stages {
        stage ('Build CI Project') {
            steps {
                
               bat  'mvn clean install'

            }

            post{
                success{                    

                    archiveArtifacts artifacts : '**/*.war'
                }
            }
        }

        stage ('Deploy Build in Dev CD Project'){
            steps{

                build job : 'Dev-CD-Project'

            }
        }

        stage ('Deploy to Production'){
            steps{
                timeout (time: 5, unit:'DAYS'){
                    input message: 'Approve PRODUCTION Deployment?'
                }
                
                build job : 'prod-cd-project'
            }

            post{
                success{
                    echo 'Deployment on PRODUCTION is Successful'
                }

                failure{
                    echo 'Deployement Failure on PRODUCTION'
                }
            }
        }
    }
}
