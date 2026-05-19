pipeline {
    agent any

    stages {
        stage ('Build') {
            steps {
                sh './mvnw clean install'
            }
            post {
                success {
                    junit 'target/surefire-reports/**/*.xml'
                }
            }
        }
    }
}
