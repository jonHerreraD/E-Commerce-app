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
        stage("Merge to Test"){
            when{
                branch 'dev1'
            }
            steps{
                sh '''
                    git checkout test1
                    git merge dev1
                    git push origin test1
                '''
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