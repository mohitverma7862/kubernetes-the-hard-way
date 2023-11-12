pipeline {
    agent any
    stages {
        stage('Scan Git Repository for Branches') {
            steps {
                script {
                    def gitRepoUrl = 'https://github.com/mohitverma7862/kubernetes-the-hard-way'
                    
                    // Use 'git ls-remote' to list all branches in the repository
                    def branches = sh(script: "git ls-remote --heads ${gitRepoUrl} | cut -d/ -f3", returnStdout: true).trim().split('\n').toList()
                    
                    // Provide the user with a dropdown list of available branches
                    def branchChoice = input(
                        id: 'branchChoice', message: 'Select a Git branch to build:',
                        parameters: [choice(name: 'BRANCH_NAME', choices: branches, description: 'Choose the branch to build')]
                    )
                }
            }
        }
        stage('Checkout to the New Branch') {
            steps {
                script {
                    def branch = sh(script: "git branch", returnStdout: true).trim()
                    echo "Current branch is ${branch}"
                    sh 'git checkout ${BRANCH_NAME}'
                }
            }
        }
        satge ('Clean The WS') {
            steps {
                ws {
                    sh 'git clean -fdx'
                }
            }
        }
    }
}
