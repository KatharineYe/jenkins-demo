pipeline {
  agent any
  stages {
    stage('build') {
      parallel {
        stage('build1') {
          steps {
            sh 'mvn -DskipTests clean package'
            sh 'echo "build###"'
            sh '''
                    echo "Multiline shell steps works too"
                    ls -lah
                '''
          }
        }

        stage('build2') {
          steps {
            echo 'aaa'
          }
        }

      }
    }

    stage('Test') {
      steps {
        echo 'Testing...'
        sh 'java -jar target/jenkins-demo-1.0-SNAPSHOT-jar-with-dependencies.jar'
      }
    }

    stage('Deploy') {
      steps {
        echo 'Deploy...'
      }
    }

  }
  post {
    always {
      echo 'This will always run'
    }

    success {
      echo 'This will run only if successful'
    }

    failure {
      echo 'This will run only if failed'
    }

    unstable {
      echo 'This will run only if the run was marked as unstable'
    }

    changed {
      echo 'This will run only if the state of the Pipeline has changed'
      echo 'For example, if the Pipeline was previously failing but is now successful'
    }

  }
  triggers {
    pollSCM('H/2 * * * *')
  }
}