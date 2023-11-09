pipeline{
    agent any
    properties([
        parameters([
            string(name: 'BRANCH_NAME', description: 'Git Branch Name', defaultValue: 'master')
        ])
    ])
    stages {
        stage ('Clone The Code Form $BRANCH_NAME') {
            checkout([$class: 'GitSCM', branches: [[name: "*/${params.BRANCH_NAME}"]]])
        }
    }
}
