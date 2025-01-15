pipeline {
    agent any

    environment {
        EC2_IP = '13.41.81.135'
    }

    stages {
        stage ('fetch code') {
            steps {
                script {
                    echo "Pull source code from Github"
                    git branch: 'main', url: 'https://github.com/ayofagbuaro/jenkins_deploy_ec2.git'
                }
            }
        }
        stage('deploy to EC2') {
            steps {
                script {
                    echo "Deploying shell script to EC2 instance"
            
                    def shellCmd = "bash /home/ubuntu/websetup.sh"
            
                    sshagent(['ec2-server']) {
                    // SCP to transfer the shell script to EC2 instance
                        sh "scp -o StrictHostKeyChecking=no ./websetup.sh ubuntu@${EC2_IP}:/home/ubuntu"

                    // SSH to EC2 to execute the shell script
                        sh "ssh -o StrictHostKeyChecking=no ubuntu@${EC2_IP} ${shellCmd}"
            }
        }
    }
}

        
        // stage ('deploy to EC2') {
        //     steps {
        //         script {
        //             echo "deployng to shell-script to ec2"
        //             def shellCmd = "bash ./websetup.sh"
        //             sshagent (['ec2-server']) {
        //                 sh "scp -o StrictHostKeyChecking=no websetup.sh ubuntu@${EC2_IP}:/home/ubuntu"
        //                 sh "ssh -o StrictHostKeyChecking=no ubuntu@${EC2_IP} ${shellCmd}"
        //             }
        //         }
        //     }
        // }
    }
}