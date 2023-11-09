pipeline {
    agent any

    parameters {
        string(name: 'BRANCH_NAME', description: 'Enter the Git branch name to clone', defaultValue: 'master')
    }

    stages {
        stage('Clone Git Repository') {
            steps {
                script {
                    // Define the Git repository URL
                    def gitRepoUrl = 'https://github.com/mohitverma7862/kubernetes-the-hard-way'

                    // Use the BRANCH_NAME parameter to specify the branch to clone
                    def branchName = params.BRANCH_NAME

                    // Clone the specified branch
                    checkout([$class: 'GitSCM', branches: [[name: "*/$branchName"]], userRemoteConfigs: [[url: gitRepoUrl]]])
                }
            }
        }

        stage('Build and Deploy') {
            steps {
                // Add your build and deployment steps here
                sh 'echo "Build and deploy code from branch: $BRANCH_NAME"'
            }
        }
    }
}
