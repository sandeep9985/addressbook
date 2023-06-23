pipeline {
    agent any
    parameters{
        string(name:'ENV',defaultvalue:'test',description:'version to deploy')
        booleanparam(name:'executetest',defaultvalue:true,description:'test executed')
        choice(name:'Appversion',choices:['1.1','1.2','1.3'])
    }
   

    stages {
        stage('Build') {
            steps {
                echo "executed build command"
                echo "deploy the env: ${params.ENV}"
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
