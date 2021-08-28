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
          def issue = sh(returnStdout: true, script: "git log -1 --pretty=%B | cut -f2 -d '#'").trim()
	  echo "Issue ${issue}"
          def hash = sh(returnStdout: true, script: "git log -1 --format=%H").trim().substring(0,7)
          echo "Hash ${hash}"
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
