pipeline {
    agent any
    stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
                // sh 'mvn clean'
                // echo 'dale!'
            }
            // post {
            //     success {
            //         echo 'Now Archiving...'
            //         archiveArtifacts artifacts: '**/target/*.war'
            //     }
            // }
        }
        stage ('Deploy to staging'){
            steps{
                build job: 'sft-deploy-stage'
            }
        }
    }
}
