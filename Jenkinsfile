pipeline {
    agent any
    tools {
        jdk 'Myjava'
        maven 'mymaven'
    }
   

    stages {
        stage('Compile') {
            
            steps {
                script {
                    sh 'mvn compile'
                    echo "executed build command"
                }
            }

           
        }
        stage('UnitTest') {
           
            steps {
                script {
                    sh 'mvn test'
                    echo "executed Test command"
                }
            post {
                always {
                     junit 'target/surefire-reports/*.xml'
                }
            }
            }

           
        }
        stage('Package') {
            
            steps {
                script {
                    sh 'mvn package'
                    echo "packaging the app"
                }
            }

           
        }
    }
}
