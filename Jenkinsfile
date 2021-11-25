pipeline {
    agent any

    environment {
        REPO_URL = 'https://github.com/martin-pineiro-glob/dtraining.git'
        REPO_WORKING_DIR = 'tempRepoDir'
        APPCENTER_TOKEN = '461035e3fe44bb713a1f4f07f5075020ed506209'
        APK_DIR = 'tempRepoDir/app/build/outputs/apk/release/app-release.apk'
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
                    sh 'chmod +x gradlew'
                    sh './gradlew clean :app:assembleRelease'
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
                echo 'Deploying to appcenter....'
                sh 'ls'
                sh 'pwd'
                appCenter apiToken: APPCENTER_TOKEN,
                          ownerName: 'Martín Piñeiro Vázquez',
                          appName: 'dtraining test app',
                          pathToApp: APK_DIR,
                          distributionGroups: 'internal'
            }
        }
    }
}