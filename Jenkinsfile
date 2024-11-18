pipeline {
    agent any

    environment {
        // Configuration de l'email
        RECIPIENT_EMAIL = 'vmokrimmohamed2016@gmail.com'
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

        stage('Envoi d\'email') {
            steps {
                script {
                    // Envoi de l'email de notification
                    emailext(
                        subject: "Test de Jenkins - Notification",
                        body: "Le pipeline Jenkins a été exécuté avec succès.",
                        to: "${RECIPIENT_EMAIL}"
                    )
                }
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
            emailext(
                subject: "Échec du pipeline Jenkins",
                body: "Le pipeline Jenkins a échoué. Veuillez vérifier les logs pour plus de détails.",
                to: "${RECIPIENT_EMAIL}"
            )
        }
    }
}
