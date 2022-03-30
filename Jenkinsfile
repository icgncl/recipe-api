pipeline{
    agent any
    stages{
        stage("A"){
            steps{
                echo "========executing A========"
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
            
            agent {
                docker {
                    image 'python:2-alpine' 
                }
            
            steps{
                withEnv(["HOME=${env.WORKSPACE}"]) {
                sh 'sudo easy_install pip; pip install docker-compose'
                }
            }
        }
        stage("C"){
            steps{
                sh 'docker-compose run app sh -c "python manage.py test && flake8"'
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