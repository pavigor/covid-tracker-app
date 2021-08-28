pipeline {
  agent any
  environment {
    TAG_NAME = sh(returnStdout: true, script: "git tag --contains").trim()
  }

  stages {
    stage('Test') {
      steps {
        echo "Test!"
      }
    }
    stage('Build') {
      steps {
	script {
          def tag = sh(returnStdout: true, script: "git tag --contains").trim()
          echo "${tag}"
	}
      }
    }
    stage('Deploy') {
      when { buildingTag() }
      steps {
        echo "Deploy by tag!"
      }
    }
  }
}
