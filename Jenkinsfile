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
                gitClonePub 'https://github.com/Rahul7-77/jenkins-sl-test.git'
            }
        }
        stage('Compile'){
            steps{
                npmBuild()
            }
        }
        stage('OWASP Scan'){
            owaspscan()
        }
        stage('Docker Build'){
            buildimage 'jsl:v1'
        }
    }
}