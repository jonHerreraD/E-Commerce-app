pipeline {
    agent any

    environment {
        GIT_CREDENTIALS = credentials('GIT_TOKEN')
    }

    stages {
        stage("Build") {
            when {
                branch 'dev1'
            }
            steps {
                echo "Building"
            }
        }
        stage("Merge to Test") {
            when {
                branch 'dev1'
            }
            steps {
                withCredentials([string(credentialsId: 'GIT_TOKEN', variable: 'TOKEN')]) {
                    sh '''
                        git config user.name "$GIT_USERNAME"
                        git config user.email "$GIT_EMAIL"
                        git remote set-url origin https://$TOKEN@github.com/jonHerreraD/E-Commerce-app.git
                        git checkout test1
                        git merge origin/dev1
                        git push origin test1
                    '''
                }
            }
        }

        stage("test") {
            when {
                branch 'test1'
            }
            steps {
                echo "Testing"
            }
        }
        stage("Pushing") {
            when {
                branch 'main'
            }
            steps {
                echo "Push"
            }
        }
    }

}
