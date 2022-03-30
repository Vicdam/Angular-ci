pipeline {
    agent {
    // this image provides everything needed to run Cypress
    docker {
      image 'cypress/base:16.13.0'
    }
  }

    tools {nodejs "node"}

    parameters {
        string(name: 'SPEC', defaultValue: 'cypress/integration/1-getting-started', description: 'Ej: cypress/integration/1-getting-started/*.spec.js')
    }

    stages {
        stage('Dependencies') {
            steps {
                sh 'npm install'
                sh 'npm run cy:verify'
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
                sh "npm run test:ci:record"
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
