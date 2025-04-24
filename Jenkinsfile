pipeline {
    agent any


    stages {
        stage('Clone') {
            steps {
                git url: 'https://github.com/MaciejSerafin/simple-webapp.git', branch: 'master'
            }
        }

        stage('Build') {
            steps {
                sh 'docker build -t simple-webapp .'
            }
        }

        stage('Test') {
            steps {
                sh 'docker run --rm simple-webapp python test.py'
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker run -d -p 5000:5000 simple-webapp'
            }
        }

        stage('Publish') {
            steps {
                archiveArtifacts artifacts: '**/*.py', fingerprint: true
            }
        }
    }
}
