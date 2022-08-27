pipeline {
  agent any
   stages {
    stage('Build') {
      steps {
        sh ''' #!/bin/bash
        python3 -m venv test3
        source test3/bin/activate
        pip install pip --upgrade
        pip install requirements.txt
        export FLASK_APP=application
        flask run &
        deactivate
        ''' 
      }
    stage('test') {
      steps {
        sh ''' #!/bin/bash 
        python3 -m venv test3
        source test4/bin/activate
        pip install pip --upgrade
        pip install requirements.txt
        pytest --verbose --junit-xml test-reports/results.xml
        deactivate
        ''' 
      }
      post{
        always {
          junit 'test-reports/results.xml'
        }
       
      }
    }
   }
  }
 }
