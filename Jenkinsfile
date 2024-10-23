pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/GJislaine/DevSecOps.git'
            }
        }
        stage ('Build-Maven'){
              steps{
                  echo 'building maven'
                  bat 'mvn clean package' 
              }
              }
              
        stage('Build Docker Image') {
            steps {
                echo 'Construction de l\'image Docker...'
                bat 'docker build -t devsecops .'
            }
        }

        stage('Test') {
            steps {
                bat 'mvnw.cmd test'
            }
        }

        stage('Package') {
            steps {
                bat 'mvnw.cmd package'
            }
        }
    } // Fermeture correcte du bloc stages

    post {
        always {
            archiveArtifacts artifacts: '**/target/*.jar', allowEmptyArchive: true
        }
        success {
            echo 'Le build a réussi et les tests ont été validés !'
        }
        failure {
            echo 'Le build a échoué.'
        }
    } // Fermeture correcte du bloc post
} // Fermeture correcte du bloc pipeline
