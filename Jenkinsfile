pipeline{
    agent any
        stages {
            stage('One'){
                steps{
                    echo "Hi, this is from Jenkins"
                }
            }
            stage('Two'){
                steps{
                    input("Do you want to continue?")
                }
            }
            stage('Three'){
                when{
                    not{
                        branch 'master'
                    }
                }
                steps{
                    echo "Hello, from stage 3"
                }
            }
            stage('Four'){
                parallel{
                    stage('Unit Test'){
                        steps{
                            echo "Running the unit tests..."
                        }
                    }
                    stage('Integration test'){
                        agent{
                            docker{
                                reuseNode false
                                image 'ubuntu'
                            }
                        }
                        steps{
                            echo "Running the integration tests..."
                        }
                    }
                }
            }
        }
}