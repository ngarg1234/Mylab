pipeline{
    //Directives
    agent any
    tools {
        maven 'maven'
    }

    stages {
        // Specify various stage with in stages

        // stage 1. Build
        stage ('Build'){
            steps {
                sh 'mvn clean install package'
            }
        }

        // Stage2 : Testing
        stage ('Test'){
            steps {
                echo ' testing......'

            }
        }

        // Publish your Artifact to Nexus
        stage ("Publish to Nexus") {
            steps{
               nexusArtifactUploader artifacts: [[artifactId: 'VinayDevOpsLab', classifier: '', file: 'target/VinayDevOpsLab-0.0.3-SNAPSHOT.war', type: 'war']], credentialsId: '26772ecb-ffeb-4e5c-b252-fdce79ec1791', groupId: 'com.vinaysdevopslab', nexusUrl: '13.127.180.184:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'VinayDevopsLab-SNAPSHOT', version: '0.0.3-SNAPSHOT' 
            }
        }

        stage ('Deployment'){
            steps {
                echo ' Deploying......'
            }
        }

        

        // // Stage3 : Publish the source code to Sonarqube
        // stage ('Sonarqube Analysis'){
        //     steps {
        //         echo ' Source code published to Sonarqube for SCA......'
        //         withSonarQubeEnv('sonarqube'){ // You can override the credential to be used
        //              sh 'mvn sonar:sonar'
        //         }

        //     }
        // }        
        
    }

}