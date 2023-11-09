pipeline {
    agent any
  parameters {
        string(name: 'BRANCH_NAME', description: 'Enter the branch name', defaultValue: 'main')
    }
    stages ('Clone The Repo') {
        stage {
            steps {
             checkout([$class: 'GitSCM', branches: [[name: "*/${params.BRANCH_NAME}"]]])
            }
        }
    }
}
