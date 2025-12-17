pipeline {
    agent {
        docker {
            // Image contenant Maven et Git
            image 'my-maven-git:latest'
            // Pour réutiliser le cache Maven local entre builds
            args '-v $HOME/.m2:/root/.m2'
        }
    }

    stages {
        stage('Checkout') {
            steps {
                // Nettoyer le répertoire
                sh "rm -rf *"
                // Récupérer le projet depuis GitHub
                sh "git clone https://github.com/Fatimazahrae3006/TPJavaPipeLine-FatimaZahrae.git"
            }
        }

        stage('Build') {
            steps {
                script {
                    // Naviguer dans le dossier Maven
                    dir('TPJavaPipeLine-FatimaZahrae') {
                        // Compiler et exécuter Maven
                        sh 'mvn clean test package'
                        sh "java -cp target/TPJavaPipeLine-1.0-SNAPSHOT.jar maven.Hello"
                    }
                }
            }
        }
    }
}
