pipeline {
    agent any

    parameters {
        string(defaultValue: "123", description: 'This is a parameter', name: 'PARAMETER01')
    }

    stages {
        stage('Start'){
            steps{
                    build job: 'ANOTHER_JOB_NAME', wait: false, parameters: [string(name: 'HELLO', value: String.valueOf(PARAMETER01))]
            }
        }
    }
}
