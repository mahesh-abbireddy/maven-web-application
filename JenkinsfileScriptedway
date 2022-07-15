node
{
    def mavenHome = tool name: "maven3.8.6"
    
    properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])
    
    echo "The Job name is: ${env.JOB_NAME}"
    echo "The node name is: ${env.NODE_NAME}"
    echo "The workspace path is: ${env.WORKSPACE}"
    echo "The node label is: ${env.NODE_LABELS}"
    echo "Th ebuild number is: ${env.BUILD_NUMBER}"
 
    //Pull the code from Github
    stage('CheckoutCode'){
        git branch: 'development', credentialsId: '81c1b302-2192-4f03-ad98-45b2b561bca1', url: 'https://github.com/mahesh-abbireddy/maven-web-application.git'
    }
    
    //Build with maven
    stage('Build'){
        sh "${mavenHome}/bin/mvn clean package"
    }
   /* 
    //Execute sonarcube report
    stage('ExecuteSonarQubeReport'){
    sh "${mavenHome}/bin/mvn sonar:sonar"
    }
    
    //Upload Artifacts in to nexus
    stage('UploadArtifcatsIntoNexus'){
    sh "${mavenHome}/bin/mvn deploy"
    }
    
    //Deploy Application in to Tomcat server
    stage('DeployAppIntoTomcatServer'){
    sshagent(['df325107-28fc-4e0e-8b8e-8063688dc861']) {
    sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@15.207.99.193:/opt/apache-tomcat-9.0.64/webapps/"
    }
    }
 */   
}
