pipeline {
    agent any
    parameters {
        booleanParam(defaultValue: true, description: '', name: 'boolParam')
        string(defaultValue: "TEST", description: 'What environment?', name: 'StringParam')
        // choices are newline separated
        choice(choices: 'Choice 1\nSecond Choice', description: 'Which Choice ?', name: 'ChoiceParam')
    }
    stages {
        stage('Example') {
            steps {
                echo 'Hello World'
            }
        }
        stage('Print parameters value') {
           steps {
              sh """
              echo booleanParam=${params.boolParam}
              echo StringParam=${params.ChoiceParam}
              echo ChoiceParam=${params.ChoiceParam}
              env
              "
           }
        }
    }
    post { 
        always { 
            echo 'I will always say Hello again!'
        }
    }
}
