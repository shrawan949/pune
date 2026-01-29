pipeline {
    agent any 

    parameters {
        string(name: 'ENV', defaultValue: 'DEV')
    }

    triggers {
        pollSCM('* * * * *')
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'mvn install'
            }
        }

        stage('Deployment') {
            steps {
                script {
                    if (env.ENV == 'QA') {
                        sh 'cp /root/.jenkins/workspace/mumbai/target/mumbai.war /root/apache-tomcat-11.0.15/webapps/'
                        echo "Deployment has been COMPLETED on QA!"
                    }
                    else if (env.ENV == 'UAT') {
                        sh 'cp /root/.jenkins/workspace/mumbai/target/mumbai.war /root/apache-tomcat-11.0.15/webapps/'
                        echo "Deployment has been done on UAT!"
                    }
                    else {
                        echo "No deployment for ENV = ${env.ENV}"
                    }
                }
            }
        }
    }
}

