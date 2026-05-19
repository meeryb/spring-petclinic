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
                sh './mvnw deploy -DskipTests'
            }
        }
    }
    post {
        failure {
            mail to: 'meryem.bouzoubaa@esi.ac.ma',
                 subject: "Échec du Pipeline Jenkins : ${currentBuild.fullDisplayName}",
                 body: "Une erreur est survenue dans l'une des étapes de build. Veuillez vérifier les logs sur Jenkins."
        }
    }
}
