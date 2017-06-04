pipeline {
   agent any
   parameters {
      booleanParam(defaultValue: true, description: '', name: 'boolParam')
      string(defaultValue: 'TEST', description: 'What environment?', name: 'StringParam')
      choice(choices: 'Choice 1\nSecond Choice', description: 'Which Choice ?', name: 'ChoiceParam')
   }
   import groovy.json.JsonSlurper

   def json = '''{
  "booleanParam": "${params.boolParam}",
  "StringParam": "${params.StringParam}",
  "ChoiceParam": "${params.ChoiceParam}"
}'''
   def slurped = new JsonSlurper().parseText(json)
   
   stages {
      stage('Example') {
         steps {
            echo 'Hello World'
            writeJSON file: 'output.json', json: slurped
         }
      }
      stage('Print parameters value') {
         steps {
            echo "booleanParam=${params.boolParam}"
            echo "StringParam=${params.StringParam}"
            echo "ChoiceParam=${params.ChoiceParam}"
            sh 'env'
            readJSON text: json
         }
      }
   }
   post {
      always {
         echo 'I will always say Hello again!'
      }
   }
}