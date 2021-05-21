node
{

 def mavenHome = tool name: "maven3.8.1"

  properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])

 stage('CheckoutCode')
 {
 git branch: 'development', credentialsId: '28db6fbe-6b66-48f7-b8d6-cee1df7b42a3', url: 'https://github.com/Muneeswar-DevOps/maven-web-application.git' 
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

 stage('DeployAppintoTomcatServer')
 {
 sshagent(['98de04cb-9b37-4b2f-8ece-ae5984eaedb7']) {
 sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@13.233.101.216:/opt/apache-tomcat-9.0.45/webapps/"   
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
