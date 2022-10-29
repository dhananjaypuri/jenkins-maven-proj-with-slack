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
                slackSend channel: 'jenkins', message: 'Code Test Started'
            }
            }

        stage("Build Code"){
            steps{
                slackSend channel: 'jenkins', message: 'Build Started'
                sh 'mvn package'
            }
            }

        stage("Deploy on Test Env"){
            steps{
                slackSend channel: 'jenkins', message: 'Deploying on test'
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
            slackSend channel: 'jenkins', message: 'App deployed Successfully !!!!!'
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}
