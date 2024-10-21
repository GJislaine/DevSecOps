pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Récupérer le code depuis le dépôt Git
                git branch: 'main', url: 'https://github.com/GJislaine/DevSecOps.git'
            }
        }

        stage('Build') {
            steps {
               
                 sh 'mvn clean install' 
                
            }
        }

        stage('Test') {
            steps {
               
               
                sh 'mvn test' 
                
            }
        }

        stage('Deploy') {
            steps {
               
                echo 'Déploiement en cours...'
            }
        }
    }

    post {
        success {
            echo 'Build réussi !'
        }
        failure {
            echo 'Le build a échoué.'
        }
    }
}
