// Script config
scriptDirectory = './commands'
helloScriptName = 'hello.sh'
flag = false

// Method to execute script
void executeScript(final String scriptName, String skipMessage) {
  if (skipMessage == null) {
    skipMessage = ''
  }

  def scriptPath = "${scriptDirectory}/${scriptName}"
  if (fileExists(scriptPath)) {
    sh "bash ${scriptPath}"
  } else {
    echo skipMessage
  }
}

pipeline {
  agent {
    docker {
      image 'python:latest'
    }
  }
  stages {
    stage("Execute"){
      steps {
        echo "========Script execute!========"
        flag = true
        echo "${flag}"
        // sh "print(100)"
        // executeScript(helloScriptName, "Skip script")
      }
      post {
        // 常に実行
        always {
          echo "========End build!========"
        }
        // 成功時
        success {
          echo "========Success!========"
        }
        // 失敗時
        failure {
          echo "========Failure...========"
        }
      }
    }
    stage("check") {
      steps {
        echo "========Checking========"
        sh "echo 'Hello'"
      }
    }
  }
  post {
    always {
      echo "========Finish!========"
    }
  }
}