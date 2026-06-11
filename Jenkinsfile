pipeline {
agent any

environment {
    SCANNER_HOME = tool 'SonarScanner'
}

stages {

    stage('Checkout') {
        steps {
            git branch: 'main',
                url: 'https://github.com/sapna96324/cdac_project.git'
        }
    }

    stage('Install Dependencies') {
        steps {
            sh 'npm install'
        }
    }

    stage('Build') {
        steps {
            sh 'npm run build'
        }
    }

    stage('SonarQube Analysis') {
        steps {
            withSonarQubeEnv('SonarQube') {
                sh '''
                $SCANNER_HOME/bin/sonar-scanner \
                -Dsonar.projectKey=Netflix-Clone \
                -Dsonar.projectName="Netflix Clone" \
                -Dsonar.sources=src
                '''
            }
        }
    }
}

}
