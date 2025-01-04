pipeline {
    agent any

    environment {
        EC2_IP = '35.179.180.77'
    }

    stages {
        stage ('fetch code') {
            steps {
                script {
                    echo "Pull source code from Git"
                    git branch: 'main', url: 'https://github.com/ayofagbuaro/jenkins_deploy_ec2.git'
                }
            }
        }
        
        // stage ('deploy to EC2') {
        //     steps {
        //         script {
        //             echo "deployng to shell-script to ec2"
        //             def shellCmd = "bash ./websetup.sh"
        //             sshagent (['ec2-server']) {
        //                 sh "scp -o StrictHostKeyChecking=no websetup.sh ubuntu@35.179.180.77:/home/ubuntu"
        //                 sh "ssh -o StrictHostKeyChecking=no ubuntu@35.179.180.77 ${shellCmd}"
        //             }
        //         }
        //     }
        // }
    }
}