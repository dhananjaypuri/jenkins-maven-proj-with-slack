pipeline{
    agent any

    tools {
        maven 'maven'
    }

    stages{
        stage("Test Code"){
            steps{
                echo "========Testing Code========"
                sh 'mvn --version'
                sh 'mvn test'
            }
            }

        stage("Build Code"){
            steps{
                echo "========Building Code========"
                sh 'mvn package'
            }
            }

        stage("Deploy on Test Env"){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'tomcatdetail', path: '', url: 'http://54.149.63.125:8080')], contextPath: '/app', onFailure: false, war: '**/*.war'
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
