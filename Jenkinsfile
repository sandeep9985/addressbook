pipeline {
    agent any
    tools {
        jdk 'Myjava'
        maven 'mymaven'
    }
   

    stages {
        stage('Compile') {
            
            steps {
                sh 'mvn compile'
                echo "executed build command"
               
            }

           
        }
        stage('UnitTest') {
           
            steps {
                sh 'mvn test'
                echo "executed Test command"
            }

           
        }
        stage('Package') {
            
            steps {
                sh 'mvn package'
                echo "packaging the app"
                
            }

           
        }
    }
}
