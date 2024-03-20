node {

def mavenHome = tool name: "maven3.8.6"
    
//checkout stage
stage ('gitpull'){
git branch: 'development ', credentialsId: '2fc3ce7b-e38a-48d1-9cb9-aeb14564ee25', 
url: 'https://github.com/mhrtechie/maven-web-application.git'    
}    

//Build stage
stage ('build '){
sh "$mavenHome/bin/mvn clean package"
}     
    
//Generate sonarqube report 
stage ('sonarQube Report'){
sh " $mavenHome/bin/mvn sonar:sonar " 
}    
 
//Upload Artifact to artifactory repo 
stage ('UploadArtifact into Nexus'){
sh " $mavenHome/bin/mvn deploy " 
}    

*/
//Deploy App to into tomcat server
stage('DeployintoAppTomcat'){
sshagent(['c953456e-7d10-4366-86bc-6fcc369681e0']) {
sh "scp -o StrictHostKeyChecking=no  target/maven-web-application.war ec2-user@13.233.125.95:/home/ec2-user"
}
}
*/
} //node closing 
