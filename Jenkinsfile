pipeline {
    agent {
        node {
            label 'maven'
        }
    }

    stages {
        stage('Clone') {
            steps {
               git branch: 'main', url: 'https://github.com/bestdevopsengineer/tweet-trend-new.git'
            }
        }
    }
}
