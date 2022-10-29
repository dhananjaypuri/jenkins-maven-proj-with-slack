pipeline{
    agent any
    tools {
        maven 'maven'
    }
    stages{
        stage("Test Code"){
            steps{
                echo "========Testing Code========"
                sh 'maven --verion'
            }
            }

        stage("Build Code"){
            steps{
                echo "========Building Code========"
            }
            }

        stage("Deploy on Test Env"){
            steps{
                echo "========Deploying Code on Test Server========"
            }
            }

        stage("Deploy code on Prod Env"){
            steps{
                echo "========Deploying Code on Prod Server========"
            }
            }

    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}
