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
                gitClonePub ''
            }
        }
    }
}