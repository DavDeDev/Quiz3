pipeline {
    agent any
    tools{
            maven 'MAVEN3'
    }
    triggers {
//            cron('* * * * 1') // Run every minute on Mondays
                cron('H/10 * * * 1') // Run every 10 minutes on Mondays
    }

    stages {
        stage('Build') {
            steps {
                script {
                    bat 'mvn clean install'
                }
            }
        }

        stage('Test with JaCoCo') {
                    steps {
                        script {
                            // Run Maven build and generate JaCoCo report
                            bat 'mvn clean verify jacoco:report'
                        }
                    }
                }

                stage('Publish JaCoCo Report') {
                    steps {
                        jacoco execPattern: '**/target/jacoco.exec', classPattern: '**/classes', sourcePattern: '**/src/main/java'
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
