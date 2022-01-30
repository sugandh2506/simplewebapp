node {

  try {
  
  stage('Code Checkout') { 
      // Get some code from a GitHub repository
      git 'https://github.com/sugandh2506/simplewebapp.git'

   }
   
   stage('Unit Test') { 
       withEnv(['C:/DevTools/apache-maven-3.8.4/bin']) {
      // Get some code from a GitHub repository
        sh 'mvn clean compile'
        sh 'mvn test'
        }
   }
   
   stage('Test Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archive 'target/*.jar'
   }
   
   stage('Package & Deploy') {
       withEnv(['C:/DevTools/apache-maven-3.8.4/bin']) {
            sh 'mvn package'
            sh 'curl --upload-file target/simplewebapp.war "http://root@127.0.0.1:80/manager/text/deploy?path=/byjenkins&update=true"'
       }
   }
   

} catch(e) {
	echo "Caught some exception"
	
  }  finally {
	echo "Finally Block"
	
}
    
}
