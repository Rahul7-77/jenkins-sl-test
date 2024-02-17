library identifier:'jenkins-shared-library@main',retriever:modernSCM(
    [
        $class : 'GitSCMSource',
        remote: 'https://github.com/Rahul7-77/jenkins-shared-library.git'
    ]
)

def gv

pipeline{
    agent any
    tools{
        nodejs 'MyNode'
    }
    stages{
        stage('Git Clone'){
            steps{
                git branch: 'main', changelog: false, poll: false, url: 'https://github.com/Rahul7-77/jenkins-sl-test.git'
            }
        }
        stage('Compile'){
            steps{
                script{
                    npmBuild()
                }
            }
        }
        stage('OWASP Scan'){
            steps{
                script{
                    owaspscan.call()
                }
            }
        }
        stage('Docker Build'){
            steps{
                script{
                    buildImage 'rahul7502/mydockerimages-1:js1'
                    dockerLogin 'docker-creds'
                    dockerPush 'rahul7502/mydockerimages-1:js1'
                    runImage('rahul7502/mydockerimages-1:js1',3000)
                }
            }
        }
    }
}