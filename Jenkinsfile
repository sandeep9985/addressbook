pipeline {
    agent none
    tools {
        jdk 'Myjava'
        maven 'mymaven'
    }
    environment {
        TEST_SERVER_IP='ec2-user@10.0.0.17'
    }
    stages {
        stage('Compile') {
            agent any
            steps {
                script {
                    sh 'mvn compile'
                    echo "executed build command"
                }
            }
        }
        stage('UnitTest') {
            agent any
            steps {
                script {
                    sshagent(['TEST_SERVER']) {
                        echo "TESTING THE CODE"
                        sh "scp -o StrictHostKeyChecking=no server-script.sh ${TEST_SERVER_IP}:/home/ec2-user"
                        sh "ssh -o StrictHostKeyChecking=no ${TEST_SERVER_IP} 'bash ~/server-script.sh'"
                    }
                }
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage ('Package') {
            agent {label 'linux_slave'}
            steps {
                script {
                    sh 'mvn package'
                    echo "packaging the app"
                }
            }
        }
    }
}