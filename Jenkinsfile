pipeline {
    agent any

    tools {
        maven 'Maven'
        gradle 'Gradle'
        jdk 'JDK'
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/thakurkatawa/Maven_to_gradle.git'
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Build with Gradle') {
            steps {
                sh 'gradle clean build'
            }
        }

        stage('Test (Gradle)') {
            steps {
                sh 'gradle test'
            }
        }

        stage('Run Application') {
            steps {
                sh 'java -jar build/libs/*.jar'
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
