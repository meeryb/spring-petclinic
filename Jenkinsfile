pipeline {
    agent any

    stages {
        stage('Compilation') {
            steps {
                sh './mvnw clean compile'
            }
        }
        stage('Tests Unitaires') {
            steps {
                sh './mvnw test'
            }
            post {
                success {
                    junit 'target/surefire-reports/**/*.xml'
                }
            }
        }
        stage('Couverture de code') {
            steps {
                sh './mvnw jacoco:report'
            }
        }
        stage('Documentation et Site') {
            steps {
                sh './mvnw site'
            }
        }
    }
}
