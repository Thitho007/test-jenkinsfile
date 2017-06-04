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
            script {
               my_json = '''{
  "booleanParam": "${params.boolParam}",
  "StringParam": "${params.StringParam}",
  "ChoiceParam": "${params.ChoiceParam}"
}'''
            }
            echo 'Hello World'
            writeFile file: 'output.json', text: my_json
            //def json_obj = readJSON text: json
            //writeJSON file: 'output.json', json: json_obj
         }
      }
      stage('Print parameters value') {
         steps {
            echo "booleanParam=${params.boolParam}"
            echo "StringParam=${params.StringParam}"
            echo "ChoiceParam=${params.ChoiceParam}"
            sh 'env'
            //json_obj = parseConfig(readJSON(file: 'output.json'))
            sh 'cat output.json'
         }
      }
   }
   post {
      always {
         echo 'I will always say Hello again!'
      }
   }
}