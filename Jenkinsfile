pipeline {
    agent { label 'OPENJDK-17' }
    stages {
        stage('vcs') {
            steps {
                git url: 'https://github.com/seshasaimatla/spring-petclinic.git', branch: 'main' 
            }
        }
        stage('build') {
            steps {
                sh 'mvn package'
            }
        }    
        stage('post build') {
            steps {
                archiveArtifacts artifacts: '**/target/gameoflife.war',
                    onlyIfSuccessful:  true
                junit  testResults: '**/surefire-reports/TEST-*.xml'
            }
        }
    }
}    

    
