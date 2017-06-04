pipeline {
   agent any
   parameters {
      booleanParam(defaultValue: true, description: '', name: 'boolParam')
      string(defaultValue: 'TEST', description: 'What environment?', name: 'StringParam')
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
            echo "booleanParam=${params.boolParam}"
            echo "StringParam=${params.StringParam}"
            echo "ChoiceParam=${params.ChoiceParam}"
            sh 'env'
         }
      }
   }
   post {
      always {
         echo 'I will always say Hello again!'
      }
   }
}