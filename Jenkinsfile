pipeline{
    agent any
    tools {
        nodejs 'node'
        
        
    }

    stages{
        stage('Build'){
            steps{
                echo 'Building the project...'
                sh 'npm install'
            }
        }

        stage('Test') {
    steps {
        echo 'Testing'
        sh 'CI=true npm test -- --coverage'
    }
      post {
            always {
                 clover(cloverReportDir: 'coverage', cloverReportFileName: 'clover.xml',
                   // optional, default is: method=70, conditional=80, statement=80
                   healthyTarget: [methodCoverage: 70, conditionalCoverage: 80, statementCoverage: 80],
                   // optional, default is none
                   unhealthyTarget: [methodCoverage: 50, conditionalCoverage: 50, statementCoverage: 50],
                   // optional, default is none
                   failingTarget: [methodCoverage: 0, conditionalCoverage: 0, statementCoverage: 0]
                 )
            }
        }
}

        stage('Deploy / Deliver') {
    steps {
        echo 'Deploying...'
     sh "npm run build"
    }
        post {
            always {
             archiveArtifacts artifacts: 'build/**/*', onlyIfSuccessful: true
      }
    }

}
}
}