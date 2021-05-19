def ver = BUILD_NUMBER
pipeline {
    agent {
          label 'master'
    }
    stages {
        
        stage ('checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Validate') {
            steps {
                sh 'mvn Compile'
            }
        }
        stage('Test') { 
            steps {
                sh 'mvn test' 
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml' 
                }
            }
        }
    }
}
