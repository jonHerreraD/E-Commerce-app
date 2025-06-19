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
            steps {
                withCredentials([usernamePassword(credentialsId: 'jenkins123', usernameVariable: 'GIT_USERNAME', passwordVariable: 'GIT_TOKEN')]) {
                    sh '''
                        git config user.name "$GIT_USERNAME"
                        git config user.email "example@example.com"
                        git remote set-url origin https://${GIT_USERNAME}:${GIT_TOKEN}@github.com/jonHerreraD/E-Commerce-app.git
                        git checkout test1
                        git merge origin/dev1
                        git push origin test1
                    '''
                }
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