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
                '''
				if (isWindows()) {
				bat '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                '''
				else {
				sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                '''
				}
            }
        }
		}

        stage ('Build') {
            steps {
                if (isWindows()) {
				bat 'mvn release:prepare release:perform';
				else {
				sh 'mvn release:prepare release:perform';
				}
            }
            post {
                success {
                    junit 'target/surefire-reports/**/*.xml' 
                }
            }
        }
    }
}