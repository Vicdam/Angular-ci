pipeline {
    agent any

    tools {nodejs "node"}

    parameters {
        string(name: 'SPEC', defaultValue: 'cypress/integration/1-getting-started', description: 'Ej: cypress/integration/1-getting-started/*.spec.js')
    }

    stages {
        stage('Dependencies') {
            steps {
                sh 'npm i'
            }
        }
        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }

        stage('e2e Tests') {
            steps {
                // sh 'npm run cypress:ci' //depreciated
                // sh 'npx cypress install --force'
                // sh 'node_modules/.bin/cypress open'
                // sh 'node_modules/.bin/cypress run'
                sh 'cypress run'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
