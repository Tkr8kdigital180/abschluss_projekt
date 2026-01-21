pipeline{
    agent any

    tools{
    maven 'Maven'
  }

  parameters {
        choice(name: 'ENVIRONMENT', choices: ['dev', 'prod'], description: 'Zielumgebung auswählen')
    }
    stages{
        stage("Build"){
            steps{
                echo "========Build has started========"
                dir("backend"){
                    sh 'mvn --version'
                    sh 'mvn clean package -P${params.ENVIRONMENT}'
                }
            }
            post{
                
                success{
                    echo "========Build executed successfully========"
                }
                failure{
                    echo "========Build execution failed========"
                }
            }
        }
        stage("Test"){
            steps{
                echo "========Test has started========"
            }
            post{
                
                success{
                    echo "========Test executed successfully========"
                }
                failure{
                    echo "========Test execution failed========"
                }
            }
        }
        stage("Docker Build"){
            steps{
                echo "========Docker Build & Push has started========"
            }
            post{
                
                success{
                    echo "========Docker Build & Push executed successfully========"
                }
                failure{
                    echo "========Docker Build & Push execution failed========"
                }
            }
        }
        stage("Docker push"){
            steps{
                echo "========Docker push has started========"
            }
            post{
                
                success{
                    echo "========Docker push executed successfully========"
                }
                failure{
                    echo "========Docker push execution failed========"
                }
            }
        }
        stage("Deploy Dev"){
            steps{
                echo "========Deploy to Dev has started========"
            }
            post{
                
                success{
                    echo "========Deploy to Dev executed successfully========"
                }
                failure{
                    echo "========Deploy to Dev execution failed========"
                }
            }
        }
        stage("Manual Approval"){
            steps{
                input message: 'Approve to Deploy to Prod?', ok: 'Deploy'
            }
        }
        stage("Deploy Prod"){
            steps{
                echo "========Deploy to Prod has started========"
            }
            post{
                
                success{
                    echo "========Deploy to Prod executed successfully========"
                }
                failure{
                    echo "========Deploy to Prod execution failed========"
                }
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