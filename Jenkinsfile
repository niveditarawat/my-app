pipeline {
    agent any
    tools {
        maven 'Maven 3.3.9'
        jdk 'jdk8'
    }
    stages {
        stage ('Initialize') {
            steps {
                echo "M2_HOME = ${M2_HOME}"
               
		
		bat '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${MAVEN_HOME}"
                '''
		
            
        	}
	}

        stage ('Build') {
            steps {
               
		bat 'mvn release:prepare release:perform';
				
            }
            post {
                success {
                    junit 'target/surefire-reports/**/*.xml' 
                }
            }
        }
    }
}

