pipeline {
    agent { label 'OPENJDK-11' }
    stages {
        stage('vcs') {
            steps {
                git url: 'https://github.com/seshasaimatla/spring-petclinic.git', branch: 'main' 
            }
        }
         stage ('Artifactory configuration') {
            steps {
                rtMavenDeployer (
                    id: "MAVEN_DEPLOYER",
                )
            }
         }

        stage ('Exec Maven') {
            steps {
                rtMavenRun (
                    tool: MAVEN-3.8.6, // Tool name from Jenkins configuration
                    pom: 'pom.xml',
                    goals: 'package',
                    deployerId: "MAVEN_DEPLOYER"
                )
            }
        }
        stage('post build') {
            steps {
                junit  testResults: '**/surefire-reports/*.xml'
            }
        }    
    }
}

    
