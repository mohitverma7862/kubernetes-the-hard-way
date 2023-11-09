pipeline {
    agent any

    parameters {
        string(name: 'BRANCH_NAME', description: 'Enter the Git branch name to clone', defaultValue: 'master')
    }

    stages {
        stage('Scan Git Repository for Branches') {
            steps {
                script {
                    def gitRepoUrl = 'https://github.com/mohitverma7862/kubernetes-the-hard-way'
                    
                    // Use 'git ls-remote' to list all branches in the repository
                    def branches = sh(script: "git ls-remote --heads ${gitRepoUrl} | cut -d/ -f3", returnStdout: true).trim().split('\n')
                    
                    // Provide the user with a dropdown list of available branches
                    def branchChoice = input(
                        id: 'branchChoice', message: 'Select a Git branch to build:',
                        parameters: [choice(name: 'BRANCH_NAME', choices: branches, description: 'Choose the branch to build')]
                    )
                }
            }
        }

        stage('Clone Git Repository') {
            steps {
                script {
                    def gitRepoUrl = 'https://github.com/mohitverma7862/kubernetes-the-hard-way'
                    def branchName = params.BRANCH_NAME

                    checkout([$class: 'GitSCM', branches: [[name: "*/$branchName"]], userRemoteConfigs: [[url: gitRepoUrl]])
                }
            }
        }

        stage('Build and Deploy') {
            steps {
                sh 'echo "Build and deploy code from branch: $BRANCH_NAME"'
            }
        }
    }
}
