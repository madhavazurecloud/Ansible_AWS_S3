pipeline {
    agent any
    
    tools {
        maven 'local_maven'
    }
    stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Archiving the artifacts'
                    archiveArtifacts artifacts: '**/target/*.war'
                    emailext body: 'congratulation your build is success', subject: 'success build', to: 'jrs.jyotiranjanswain@gmail.com'
                }
                failure {
                    emailext body: 'sorry your build is faild', subject: 'failure build', to: 'jrs.jyotiranjanswain@gmail.com'
                }                
            }
        }
        stage ('Deployments'){
            steps {
            echo 'successful Deploy'
            }
        }

    }
}
