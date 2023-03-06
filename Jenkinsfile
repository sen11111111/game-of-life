pipeline {
    agent { label 'jenkinsnode' }
    triggers { corn ('H/15 * * * *')  }
    stages {
        stage('versioncontrol vcs') {
            steps {
                git url: 'https://github.com/sen11111111/game-of-life.git',
                    branch: 'declarative'
            }
        }
        stage('maven package') {
             tools {
                jdk 'jdk8'
             }
            steps {
                sh 'mvn package'
            }
        }
        stage('post the build') {
            steps {
                archiveArtifacts artifacts: '**/target/gameoflife.war',
                                 onlyIfSuccessful: true
                junit testResults: '**/surefire-reports/TEST-*.xml'
            }
        }
    }
}