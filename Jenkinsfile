pipeline {
    agent {
        node {
            label 'maven'
        }
    }

    environment{
        PATH = "/opt/apache-maven-3.9.2/bin:$PATH"
    }
    stages {
        stage('build') {
            steps {
               sh 'mvn clean deploy'
            }
        }

       stage('SonarQube analysis') {
            environment {
              scannerHome = tool 'valaxy-sonar-scanner'
            }
        steps{
        withSonarQubeEnv('valaxy-sonarqube-server') { // If you have configured more than one global server connection, you can specify its name
        withEnv(["JAVA_HOME=/usr/lib/jvm/java-17-openjdk-amd64", "PATH=/usr/lib/jvm/java-17-openjdk-amd64/bin:${env.PATH}"]) {
          sh "${scannerHome}/bin/sonar-scanner"
        }
        }
        }
      }
        
    }
}
