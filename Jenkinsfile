pipeline {
    agent any

    stages {
        stage('GIT checkout') {
            steps {
                echo 'Get from GIT repository'
                git credentialsId: 'git_ssh',
                url: 'https://github.com/SlavaZakariev/vector-role-molecule.git',
                branch: 'main'
            }
        }
        stage('preparation') {
            steps {
                echo 'Start preparation'
                sh 'pip3 install -r requirements.txt'
                sh 'pip install "molecule[lint]"'
                sh 'pip install "molecule[docker,lint]"'
            }
        }
        stage('Start molecule test') {
            steps {
                echo 'Run molecule test'
                sh 'molecule test'
            }
        }
    }
}
