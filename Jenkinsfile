env.dockerimagename="devopsbasservice/buildonframework:buildon-jenkinsfile"
node {
   stage ('Banking_Build') {
   //If some other Repository is to be given apart from current repo, provide git URL as below.             
   //git url:'http://50.17.36.28/root/onlinebanking.git'            
   //CS demo
   
    checkout scm
    sh 'mvn clean package -DskipTests=True'
  }
   stage ('Banking_CodeAnalysis') {
    sh 'mvn sonar:sonar -Dsonar.host.url=http://54.209.104.148:9001/ -Dmaven.test.failure.ignore=true -DskipTests=true -Dsonar.sources=src/main/java'
   }

   stage ('Banking_NexusUpload') {
    sh 'curl -v -u admin:admin123 --upload-file /var/jenkins/jobs/$commitID/workspace/target/onlinebanking.war http://54.209.104.148:8081/nexus/content/repositories/buildonrepo/$commitID.war'
    // Test Looks like below line added as part of testing. if you uncomment, will encounter build failure due to syntax error. Ensure you give right commands and syntax
    //sh 'echo qwerty'
    sh 'echo $(uname)'
    //sh 'echo $(hostname -s)'
    //sh  'echo DNS domain $(hostname -d)'
	//sh 'echo Fully qualified domain name $(hostname -f)''
	//sh 'echo Network address (IP)   $(hostname -i)'
	//sh 'echo DNS name servers (DNS IP)  ${dnsips}'     
   } 
}
