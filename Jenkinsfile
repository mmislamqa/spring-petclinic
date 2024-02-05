pipeline{
    agent any
    triggers {pollSCM('*/2 * * * *')}
    stages{
        stage('Git Clone'){
            steps{
            git branch: 'main', url: 'https://github.com/mmislamqa/spring-petclinic.git'
            }

        }

        stage('Packaging code'){
            steps{
                sh 'mvn package'
            }
        }

        stage('Archiving Artifacts'){
            steps{
                archiveArtifacts artifacts: 'target/*jar', followSymlinks: false
            }
        }
        stage('Displaying unit test results'){
            steps{
                junit stdioRetention: '', testResults: 'target/surefire-reports/*.xml'
            }
        }
    }

}