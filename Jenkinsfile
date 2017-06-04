pipeline {
   agent any
   parameters {
      booleanParam(defaultValue: true, description: '', name: 'boolParam')
      string(defaultValue: 'TEST', description: 'What environment?', name: 'StringParam')
      choice(choices: 'Choice 1\nSecond Choice', description: 'Which Choice ?', name: 'ChoiceParam')
   }

   stages {
      stage('Set Content of file & Write it') {
         steps {
            script {
               my_json = """{
  \"booleanParam\": \"${params.boolParam}\",
  \"StringParam\": \"${params.StringParam}\",
  \"ChoiceParam\": \"${params.ChoiceParam}\"
}"""
            }
            writeFile file: 'output.json', text: my_json
         }
      }
      stage('Get Content of file') {
         steps {
            sh 'env'
            //script {
            json_obj = readJSON file: 'output.json'
            //}
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