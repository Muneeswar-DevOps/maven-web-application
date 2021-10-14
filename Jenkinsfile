node
{

 def mavenHome = tool name: "maven3.8.3" 
 
 properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])

 stage('CheckoutCode')
 {
  git branch: 'development', credentialsId: '493894d2-e211-43bb-a34a-33e3bd21b16a', url: 'https://github.com/Muneeswar-DevOps/maven-web-application.git'
 }

 stage('Build')
 {
  sh "${mavenHome}/bin/mvn clean package"
 }
 /*
 stage('ExecuteSonarQubeReport')
 {
  sh "${mavenHome}/bin/mvn sonar:sonar"
 }

 stage('UploadArtifactsintoNexus')
 {
  sh "${mavenHome}/bin/mvn deploy"
 }
 
 stage('DeployApplicationintoTomcatServer')
 {
  sshagent(['43d7efd9-8f65-4c80-a09e-768de351f0eb']) {
  sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@15.207.109.75:/opt/apache-tomcat-9.0.54/webapps/"
 }
 }
 */
 stage('SendEmailNotification')
 {
  emailext body: '''Build Over...

  Regards,
  Muneeswar''', subject: 'Build Over...', to: 'muneeswarababumacherla2021@gmail.com'
 }

}

