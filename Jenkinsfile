pipeline {
    agent any
    stages {
        stage('Start'){
            steps{
                script{                 
                //def branchname = "testme"
                // get branch name with
                def branchname = GIT_BRANCH
                def testvariable = "test"

                build job: 'input', wait: false, parameters: [string(name: 'branchname', value: branchname )]

                }
            }
        }
    }
}
