pipeline {
    agent any

    tools {
        jdk 'JDK11'
        maven 'Maven3'
    }

    triggers {
        githubPush()          // Build on GitHub push
        cron('0 2 * * *')     // Nightly build at 2 AM
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
    }

    post {
        success {
            echo 'Build successful and JAR created'
        }
    }
}
