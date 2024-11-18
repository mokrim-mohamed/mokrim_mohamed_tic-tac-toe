pipeline {
    agent any

    environment {
        // Configuration de l'email
        RECIPIENT_EMAIL = 'mokrimmohamed2016@gmail.com'
    }

    stages {
        stage('Début') {
            steps {
                echo 'Début du pipeline Jenkins'
            }
        }

        stage('Test') {
            steps {
                echo 'Exécution des tests...'
                // Ajoutez ici des étapes pour exécuter vos tests si nécessaire
            }
        }


    }

    post {
        always {
            echo 'Pipeline terminé.'
        }
        success {
            echo 'Le pipeline a réussi.'
        }
        failure {
            echo 'Le pipeline a échoué.'

        }
    }
}
