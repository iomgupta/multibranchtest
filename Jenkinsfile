pipeline {
    agent any

    stages {
        stage('Check Branch') {
            steps {
                script {
                    echo "Running on branch: ${env.BRANCH_NAME}"
                }
            }
        }
    }
}
