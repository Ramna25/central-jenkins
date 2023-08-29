pipeline {
    agent any


    stages {
        stage('Starts'){
            steps{
                script{
                def branchname = GIT_BRANCH
                build job: 'input', wait: false, parameters: [string(name: 'branchname', value: branchname )]

                }
            }
        }
    }
}
