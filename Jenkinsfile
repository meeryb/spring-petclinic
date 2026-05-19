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
        stage('Packaging') {
            steps {
                sh './mvnw package -DskipTests'
            }
        }
        stage('Déploiement') {
            steps {
                // Simule le déploiement local demandé par l'énoncé sans distributionManagement
                sh 'echo "Déploiement simulé du package dans le dépôt local de l\'entreprise"'
            }
        }
    }

    post {
        failure {
            echo "Échec du Pipeline Jenkins : Une erreur est survenue dans l'une des étapes de build."
        }
    }
}
