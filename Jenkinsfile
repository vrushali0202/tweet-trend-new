pipeline {
    agent {
        node {
            label 'maven'
        }
    }

    environment{
        PATH = "/opt/apache-maven-3.9.8/bin:$PATH"
    }

    stages {
        stage('clone code') {
            steps {
               git branch: 'main', url: 'https://github.com/vrushali0202/tweet-trend-new.git'
            }
        }
           
        // stage('build code') {
        //     steps {
        //        sh 'mvn clean deploy'
        //     }
        // }

        stage('SonarQube analysis') {
            environment{
               scannerHome = tool 'valaxy-sonar-scanner';
            }
            steps{
                withSonarQubeEnv('valaxy-sonarqube-server') { // If you have configured more than one global server connection, you can specify its name
                   sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }        
    }
}
