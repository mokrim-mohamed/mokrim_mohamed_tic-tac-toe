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

        stage('Envoi d\'email') {
            steps {
                script {
                    // Envoi de l'email de notification
                    emailext(
                        subject: "Test de Jenkins - Notification",
                        body: "Le pipeline Jenkins a été exécuté avec succès.",
                        to: "mokrimmohamed2016@gmail.com"
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
            // Envoi de l'email avec la sortie de la console en cas de succès
            script {
                def consoleOutput = currentBuild.rawBuild.getLog(1000).join("\n") // Récupère les 1000 premières lignes du log
                emailext(
                    subject: "Succès du pipeline Jenkins",
                    body: "Le pipeline Jenkins a réussi.\n\nLogs du pipeline:\n${consoleOutput}",
                    to: "${RECIPIENT_EMAIL}"
                )
            }
        }
        failure {
            echo 'Le pipeline a échoué.'
            // Envoi de l'email avec la sortie de la console en cas d'échec
            script {
                def consoleOutput = currentBuild.rawBuild.getLog(1000).join("\n") // Récupère les 1000 premières lignes du log
                emailext(
                    subject: "Échec du pipeline Jenkins",
                    body: "Le pipeline Jenkins a échoué. Veuillez vérifier les logs pour plus de détails.\n\nLogs du pipeline:\n${consoleOutput}",
                    to: "${RECIPIENT_EMAIL}"
                )
            }
        }
    }
}
