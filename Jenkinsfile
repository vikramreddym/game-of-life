pipeline {
    agent {label 'JDK8'}
    tools {
        jdk 'JDK8'
        maven '3.8.4'

    }
    stages{
        stage('SourceCode') {
            steps {
                git branch: 'scripted-declarative', url: 'https://github.com/vikramreddym/game-of-life.git'
            }
        }

        stage('Build the code'){
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Archiving artifacts & Junit test results') {
            steps {
                junit stdioRetention: '', testResults: '**/surefire-reports/*.xml'
                archiveArtifacts artifacts: '**/*.war', followSymlinks: false
            }
        }
    }
}