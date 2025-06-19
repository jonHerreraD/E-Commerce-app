pipeline{
    agent any

    stages {
        stage("Build"){
            when {
                branch 'dev1'
            }
            steps{
                echo "Building"
            }
        }
        stage("test"){
            when {
                branch 'test1'
            }
            steps{
                echo "Testing"
            }
        }
        stage("Pushing"){
            when {
                branch 'main'
            }
            steps{
                echo "Push"
            }
        }
    }
}