pipeline {
    agent any
    environment {
        SECRET_TEXT = credentials("github_secret")
    }
    stages {
        stage("install deps") {
            steps {
                bat "npm install"
            }
        }
        stage("run tests") {
            steps {
                bat "npm test"
            }
        }
        stage("package") {
            steps {
                bat "npm pack"
            }
        }
    }
    post {
        always {
            archiveArtifacts artifacts: '*.tgz', followSymlinks: false
        }
    }
}