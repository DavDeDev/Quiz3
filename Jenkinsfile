pipeline {
    agent any

    triggers {
           cron('* * * * 1') // Run every minute on Mondays
//         cron('H H * * 1') // Run every 10 minutes on Mondays
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
                echo 'Pipeline succeeded! Add any additional success steps here.'
            }

            failure {
                echo 'Pipeline failed! Add any additional failure steps here.'
            }
        }
}
