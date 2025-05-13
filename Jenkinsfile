pipeline {
    agent any

    tools {
        gradle 'Gradle' // Must match the Jenkins tool name exactly
        jdk 'JDK'       // Must match the Jenkins JDK name exactly
    }

    environment {
        JAVA_HOME = tool 'JDK'
        PATH = "${tool 'Gradle'}/bin:${env.JAVA_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/thrishaaaa/gradle'
            }
        }

        stage('Build') {
            steps {
                sh 'gradle build'
            }
        }

        stage('Test') {
            steps {
                sh 'gradle test'
            }
        }

        stage('Run Application') {
            steps {
                sh 'gradle run'
            }
        }
    }

    post {
        success {
            echo 'Build and deployment successful!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}

