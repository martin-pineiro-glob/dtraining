pipeline {
    agent any

    environment {
        REPO_URL = 'https://github.com/martin-pineiro-glob/dtraining.git'
        REPO_WORKING_DIR = 'tempRepoDir'
    }

    stages {

        stage('Clone') {
            steps {
                echo 'Cloning repo...'
                dir(REPO_WORKING_DIR) {
                    git url: REPO_URL, branch: 'dev', credentialsId: 'usergit'
                }
            }
        }
        stage('Build') {
            steps {
                echo 'Building..'
                dir(REPO_WORKING_DIR) {
                    sh './gradlew clean '
                }
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}