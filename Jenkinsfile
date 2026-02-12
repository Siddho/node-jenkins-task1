pipeline {
    agent any
    stages {
        stage('Build') {
            steps { bat 'npm install && npm run build' }
        }
        stage('Unit and Integration Tests') {
            steps { bat 'npm test' }
        }
        // stage('Code Analysis') {
        //     steps { bat 'sonar-scanner' }
        // }
        stage('Security Scan') {
            steps { bat 'dependency-check.bat --scan .' }
        }
        stage('Deploy to Staging') {
            steps { bat 'aws deploy ...' }
        }
        stage('Integration Tests on Staging') {
            steps { bat 'newman run collection.json' }
        }
        stage('Deploy to Production') {
            steps { bat 'aws deploy ...' }
        }
    }
}
