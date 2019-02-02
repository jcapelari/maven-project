pipeline {
    agent any
    stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage ('Deploy to staging'){
            steps{
                timeout(time:5, unit:'DAYS') {
                    input message: 'Approve it baby...'
                }

                build job: 'sft-deploy-stage'
            }
        }
        stage ('Deploy to prod'){
            steps{
                echo 'PROD ;-)'
            }
        }
    }
}
