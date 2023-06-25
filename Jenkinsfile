pipeline {
    agent any
    parameters{
        string(name:'ENV',defaultValue:'test',description:'version to deploy')
        booleanParam(name:'executetest',defaultValue:true,description:'test executed')
        choice(name:'Appversion',choices:['1.1','1.2','1.3'])
    }
    environment{
        NEW_VERSION = '2.1'
    }
   

    stages {
        stage('Build') {
            input{
                message "select the appversion"
                OK "version selected"
                parameters{
                    choice(name:'appversion',choices:['1.1','1.2','1.3'])
                }
            }
            steps {
                echo "executed build command"
                echo "deploy the env: ${params.ENV}"
                echo "our newversion is: ${NEW_VERSION}"
            }

           
        }
        stage('TEST') {
            when {
                expression{
                    params.executetest == true
                } 
            }
            steps {
                echo "executed Test command"
            }

           
        }
        stage('Deploy') {
            
            steps {
                echo "executed deploy command"
                echo "deploy the appversion: ${params.Appversion}"
            }

           
        }
    }
}
