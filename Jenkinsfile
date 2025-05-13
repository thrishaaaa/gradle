pipeline {
    agent any

    tools {
        gradle 'Gradle'
        jdk 'JDK'
    }

    environment {
        JAVA_HOME = tool(name: 'JDK', type: 'hudson.model.JDK')
        PATH = "${tool 'Gradle'}/bin:${JAVA_HOME}/bin:${env.PATH}"
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
}

