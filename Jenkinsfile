node{
    
def mavenhome = tool name: "maven3.6.3"

stage('checkoutcode')
{
git branch: 'development', credentialsId: '3620f580-d3ca-4f5d-8d66-3f0956472699', url: 'https://github.com/Murali-Grahitha-org/maven-web-application.git'
}
stage('build')
{
sh "${mavenhome}/bin/mvn clean package"
}
stage('sonarqube')
{
sh "${mavenhome}/bin/mvn sonar:sonar"
}
stage('deploytonexus')
{
sh "${mavenhome}/bin/mvn deploy"
}
stage('deploytotomcat')
{
sshagent(['29082b06-a492-4d7a-af83-3a840b8c88f6'])
{
 sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@13.232.196.228:/opt/apache-tomcat-9.0.39/webapps"
}}}
