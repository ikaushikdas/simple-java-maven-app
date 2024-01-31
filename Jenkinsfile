pipeline {
    agent any

    tools {
        maven 'MAVEN'
    }
    
    stages {
        stage('Build') {
            steps {
                script {
                    // Build the project
                    sh 'mvn clean install'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    // Run tests
                    sh 'mvn test'
                }
            }
        }
    }
    post {
        cleanup {
            deleteDir()
            dir("${env.WORKSPACE}@tmp") {
                deleteDir()
            }
            dir("${env.WORKSPACE}@script") {
                deleteDir()
            }
            dir("${env.WORKSPACE}@script@tmp") {
                deleteDir()
            }
        }
    }
}
