
pipeline{
    tools{
       
        maven 'mymaven'
    }
	agent any
      stages{
           stage('Checkout'){
	    
               steps{
		 echo 'cloning'
                 git 'https://github.com/chetana1910/spring-boot-war-example.git'
              }
          }
          stage('Compile'){
             
              steps{
                  echo 'complie the code..'
                  sh 'mvn compile'
	      }
          }
          stage('CodeReview'){
		  
              steps{
		    
		  echo 'codeReview'
                  sh 'mvn pmd:pmd'
              }
          }
           stage('UnitTest'){
		  
              steps{
	         
                  sh 'mvn test'
              }
          
          }
        
          stage('Package'){
		  
              steps{
		  
                  sh 'mvn package'
              }
          }
	  
	      stage ('Deploy'){
		      
		      steps {
			      script {
				      
		      deploy adapters: [tomcat9(credentialsId: 'tomcat_cred', path: '', url: 'http://54.196.175.55:8090')], contextPath: 'webapp', onFailure: false, war: '**/*.war'
			      }
		      }
		      
	      }    
      }
}
