pipeline {
  // 设置全局变量
  environment {}
  agent all
  stages {
    // 进行maven构建
    stage('Build jar file') {
        steps {
            sh 'mvn -DskipTests clean package'
        }
    }

    // 部署
    stage('Deploy Environment') {
        steps {
            sh 'java -jar target/jenkins-demo-1.0-SNAPSHOT-jar-with-dependencies.jar'
        }
    }
  }
}