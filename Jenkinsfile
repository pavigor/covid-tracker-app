pipeline {
  agent any

  stages {
    stage('Test') {
      step {
        echo "Test!"
      }
    }
    stage('Build') {
      steps {
        step {
          def tag = sh(returnStdout: true, script: "git tag --sort version:refname | tail -1").trim()
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
