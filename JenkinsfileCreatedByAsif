node{

echo "The Job name is: ${env.JOB_NAME}"
echo "The Node name is: ${env.NODE_NAME}"
echo "The Build number is: ${env.BUILD_NUMBER}" 

properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '10', daysToKeepStr: '', numToKeepStr: '10')), pipelineTriggers([pollSCM('* * * * *')])])

def mavenHomepath = tool name: 'maven3.9.9'

stage('GettingAcode'){
git branch: 'development', credentialsId: 'c07569c0-672e-4c94-be6a-c6e0b3bd961a', url: 'https://github.com/asifpashaj-slice/maven-web-application.git'
}

stage('Build'){
sh "${mavenHomepath}/bin/mvn clean package"
}
/*
stage('ExecuteSonarqubeReport'){
sh "${mavenHomepath}/bin/mvn clean package sonar:sonar"
}

stage('UploadArtifactsIntoNexus'){
sh "${mavenHomepath}/bin/mvn clean deploy"
}

stage('DeployAppIntoTomcatServer') {
    sshagent(['4ec860a7-d7d3-4c5a-8874-0739c4dc5999']) {
        sh '''scp -o StrictHostKeyChecking=no target/maven-web-application.war root@172.31.31.234:/opt/tomcat9/webapps'''
    }
}

*/
}
