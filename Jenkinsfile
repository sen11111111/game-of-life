pipeline {
    agent { label 'jenkinsnode' } 
    parameters {
        choice(name: 'maven_dick', choices: ['package', 'install'], description: 'maven_package?') 
    }
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
                sh "mvn ${maven_dick}"
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