pipeline {
  agent any
  stages {
    stage("build"){
      steps {
        echo "Start build!"
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
        echo "Checking"
      }
    }
  }
  post {
    always {
      echo "========Finish!========"
    }
  }
}