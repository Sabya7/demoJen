pipeline {
  agent any
  stages {
    stage('Build13') {
      parallel {
        stage('Build13') {
          post {
            success {
              archiveArtifacts(artifacts: '/target/*.*', fingerprint: true)
            }

          }
          steps {
            echo 'Hello Sabya'
            bat 'mvn clean compile package'
          }
        }

        stage('AntBuild13') {
          post {
            success {
              archiveArtifacts(artifacts: '/target/*.*', fingerprint: true)
            }

          }
          steps {
            bat 'mvn ant:ant'
            withAnt(installation: 'Default') {
              bat 'ant compile jar'
            }

          }
        }

      }
    }

  }
}