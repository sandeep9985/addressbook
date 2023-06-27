pipeline {
    agent none
    tools {
        jdk 'Myjava'
        maven 'mymaven'
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
                    sh "ssh -o StrictHostKeyChecking=no ec2-user@10.0.0.17 'mvn test'"
                    }
                }
           
            }
            post {
                always {
                     junit 'target/surefire-reports/*.xml'
                }
            }
           
        }
        stage('Package') {
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
