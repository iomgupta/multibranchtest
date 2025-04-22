pipeline {
    agent any

    stages {
        stage('Branch Check') {
            steps {
                script {
                    if (env.BRANCH_NAME == 'development') {
                        echo "Executing pipeline for development branch..."
                    } else if (env.BRANCH_NAME == 'deployment') {
                        echo "Executing pipeline for deployment branch..."
                    } else if (env.BRANCH_NAME == 'release') {
                        echo "Executing pipeline for release branch..."
                    } else if (env.BRANCH_NAME == 'test') {
                        echo "Executing pipeline for test branch..."
                    } else {
                        error "Branch ${env.BRANCH_NAME} is not configured for this pipeline."
                    }
                }
            }
        }

        stage('Build Applications') {
            parallel {
                stage('Build Linux Application') {
                    steps {
                        echo "Building Linux application on branch: ${env.BRANCH_NAME}"
                    }
                }
                stage('Build Windows Application') {
                    steps {
                        echo "Building Windows application on branch: ${env.BRANCH_NAME}"
                    }
                }
            }
        }

        stage('Build Executables') {
            parallel {
                stage('Build Executable Linux Application') {
                    steps {
                        echo "Building executable Linux application on branch: ${env.BRANCH_NAME}"
                    }
                }
                stage('Build Executable Windows Application') {
                    steps {
                        echo "Building executable Windows application on branch: ${env.BRANCH_NAME}"
                    }
                }
            }
        }

        stage('Yocto Build') {
            steps {
                echo "Running Yocto build on branch: ${env.BRANCH_NAME}"
            }
        }
    }
}
