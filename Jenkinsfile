env.dockerimagename="devopsbasservice/buildonframework:buildon-jenkinsfile"
node {
   stage ('SP_Clinic_Build') {
    checkout scm
    sh 'mvn clean package -DskipTests=True'
  }
  }
