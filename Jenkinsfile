pipeline {
    agent any
    tools {
        maven 'Maven 3.3.9'
        jdk 'jdk8'
    }
    stages {
        stage ('Initialize') {
            steps {
		    script {
			    echo "M2_HOME = ${M2_HOME}"
			    if(isUNix()){
				 sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                '''   
			    } else {
				bat '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                '''    
			    }
                       
		
                    }
                
		}
		
		
            
        	}
	

        stage ('Build') {
            steps {
               script {
		bat 'mvn clean install';
		   //maven release plugin can be used to auto increment version and and to push to local repository or remote  exus repository
		
		  bat '''
                  mvn clean install
                '''
	       }
		}
		}
		}
            post {
                success {
                    junit 'target/surefire-reports/**/*.xml' 
                }
            }
        
    }

