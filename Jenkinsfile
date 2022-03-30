pipeline{
    agent any
    stages{
        stage("A"){
            steps{
                sh '''
                    docker info
                    docker version
                    docker compose version
                    curl --version
                    jq --version
                '''
            }
            post{
                always{
                    echo "========always========"
                }
                success{
                    echo "========A executed successfully========"
                }
                failure{
                    echo "========A execution failed========"
                }
            }
        }
        stage("B"){
            steps{
                echo "It is done"
            }
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}
