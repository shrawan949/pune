pipeline {
  agent any
 
  parameters {
      string defaultValue: 'DEV' ,name: 'ENV'
   }
  triggers{
      pollSCM '* * * * *'
}
 stages {
   stage('checkout') {
     steps  checkout scm
 }}
  stage('Build') {
   steps {
      sh 'mvn install'
  }}
  stage('Deployment'){
   steps{
      script{
        if (env.ENV == 'QA'){
    sh 'cp /root/.jenkins/workspace/maharastra/target/maharastra.war  /root/apache-tomcat-11.0.15/webapps'
    echo "deployment has been COMPLETED on QA!"
  }
        else (env.ENV == 'UAT'){
    sh 'cp /root/.jenkins/workspace/maharastra/target/maharastra.war  /root/apache-tomcat-11.0.15/webapps'
    echo "deployment has been COMPLETED on UAT!"
  }
}
}

