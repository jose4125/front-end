pipeline{
    agent any
    tools{
      nodejs 'NodeJs 13.11.0'
    }
    stages{
        stage("build"){
            steps{
                echo "======== executing Build ========"
                sh 'npm install'
            }
            post{
                success{
                    echo "======== Build executed successfully ========"
                }
                failure{
                    echo "======== Build execution failed ========"
                }
            }
        }
        stage("test"){
            steps{
              echo "======== executing Test ========"
              sh 'npm run test'
            }
            post{
                success{
                    echo "======== Test executed successfully ========"
                }
                failure{
                    echo "======== Test execution failed ========"
                }
            }
        }

        stage("package"){
            steps{
              echo "======== executing Package ========"
              sh 'npm run package'
              archiveArtifacts artifacts: '**/distribution/*.zip', fingerprint: true
            }
        }
    }
}
