pipeline {
    agent any

    environment {
        // Define environment variables if needed
        JAVA_HOME = tool name: 'Java', type: 'jdk'
        MAVEN_HOME = tool name: 'Maven', type: 'maven'
    }

    stages {
        stage('Checkout') {
            steps {
                // Check out the code from the GitHub repository
                script {
                    def gitCredentials = credentials('your-github-credentials-id')
                    checkout([$class: 'GitSCM',
                        branches: [[name: '*/main']], // Adjust the branch name
                        userRemoteConfigs: [[url: 'https://github.com/swetamishra123/Netflixclone.git', credentialsId: gitCredentials]]
                    ])
                }
            }
        }

        stage('Build') {
            steps {
                // Build your Maven project
                sh "${tool(name: 'Maven', type: 'maven')}/bin/mvn clean package"
            }
        }

        stage('Test') {
            steps {
                // Run tests using Maven
                sh "${tool(name: 'Maven', type: 'maven')}/bin/mvn test"
            }
        }

        stage('Deploy') {
            steps {
                // Deploy your application (e.g., to a server)
                // Replace this with your deployment steps
            }
        }
    }

    post {
        success {
            // Notify or perform actions on success
        }

        failure {
            // Notify or perform actions on failure
        }
    }
}
