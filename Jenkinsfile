pipeline {
    agent any

    triggers {
        cron('H H * * 1') // Run every 10 minutes on Mondays
    }

    stages {
        stage('Build') {
            steps {
                script {
                    sh 'mvn clean install'
                }
            }
        }

        stage('Code Coverage') {
            steps {
                script {
                    // Jacoco setup and execution
                    sh 'mvn jacoco:prepare-agent test jacoco:report'
                }
            }
        }
    }

    post {
        success {
        }

        failure {
        }
    }
}
