pipeline {
    agent any

    stages {
        stage('Clone repository') {
            steps {
                git 'https://github.com/Meenakshi0812/automatic-branch-create-delete.git'
            }
        }

        stage('Branch creation') {
            steps {
                script {
                    def branchName = "new-branch-${env.BUILD_ID}"
                    sh "git checkout -b ${branchName}"
                    sh "git push origin ${branchName}"
                }
            }
        }

        stage('Perform build and tests') {
            steps {
                // Add your build and test commands here
            }
        }

        stage('Branch deletion') {
            steps {
                script {
                    def branchName = "new-branch-${env.BUILD_ID}"
                    sh "git push origin --delete ${branchName}"
                }
            }
        }
    }

    post {
        always {
            cleanWs() // Clean workspace
        }
    }
}
