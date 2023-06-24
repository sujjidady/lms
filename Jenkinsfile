@Library ("raj-lib") _
pipeline {
    agent any

    stages {
        stage('git checkout') {
            steps {
                git branch: 'main', credentialsId: 'sujji-git-clone', url: 'https://github.com/sujjidady/lms'
            }
        }
        
         stage('maven build') {
            steps {
                sh 'mvn clean package'
            }
        }
        
        stage('dev deploy') {
            steps {
                tomcatDeploy("ec2-user","172.31.14.74","tom","lms")
                
            }
        }
    }
}
