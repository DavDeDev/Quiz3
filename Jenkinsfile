pipeline {
    agent any
    tools{
            maven 'MAVEN3'
    }
    triggers {
//            cron('* * * * 1') // Run every minute on Mondays
        cron('H H * * 1') // Run every 10 minutes on Mondays
    }

    stages {
        stage('Build') {
            steps {
                script {
                    bat 'mvn clean install'
                }
            }
        }

        stage('Code Coverage') {
            steps {
                script {
                    // Jacoco setup and execution
                    bat 'mvn jacoco:prepare-agent test jacoco:report'
                }
            }
        }
    }

    post {
            success {
                echo 'Pipeline succeeded!'
            }

            failure {
                echo 'Pipeline failed!'
            }
        }
}
