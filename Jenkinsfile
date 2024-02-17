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
                // script{
                //     gitClonePub 'https://github.com/Rahul7-77/jenkins-sl-test.git'
                // }
                sh 'git clone https://github.com/Rahul7-77/jenkins-sl-test.git'
            }
        }
        stage('Compile'){
            steps{
                script{
                    npmBuild()
                }
            }
        }
        // stage('OWASP Scan'){
        //     steps{
        //         script{
        //             owaspscan()
        //         }
        //     }
        // }
        stage('Docker Build'){
            steps{
                script{
                    buildimage 'jsl:v1'
                }
            }
        }
    }
}