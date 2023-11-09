pipeline {
    properties([
        parameters([
            string(name: 'SERVER_NAME', description: 'Server Name or IP', defaultValue: 'your-server-ip'),
            string(name: 'BRANCH_NAME', description: 'Git Branch Name', defaultValue: 'master')
        ])
    ])

    node {
        stage('Checkout') {
            checkout([$class: 'GitSCM', branches: [[name: "*/${params.BRANCH_NAME}"]]])
        }
    }
}
