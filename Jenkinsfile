pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'maven:3.9.6-eclipse-temurin-17'
    }

    stages {
        stage('Checkout SCM') {
            steps {
                // Récupérer le code depuis GitHub
                checkout scm
            }
        }

        stage('Build') {
            steps {
                // Utiliser Docker pour exécuter Maven
                script {
                    docker.image(env.DOCKER_IMAGE).inside {
                        sh 'mvn clean install'
                    }
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    docker.image(env.DOCKER_IMAGE).inside {
                        sh 'mvn test'
                    }
                }
            }
        }

        stage('Results') {
            steps {
                echo 'Build et tests terminés.'
                sh 'ls -l target'
            }
        }
    }
}
