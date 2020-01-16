pipeline {
  agent any
  stages {
    stage('Build13') {

      parallel {
        stage('Build13') {
          steps {
            echo 'Hello Sabya'
            bat 'mvn clean compile'
          }
          post {
                  always {
                      archiveArtifacts artifacts: '/target/*.*', fingerprint: true
                      junit 'build/reports/**/*.xml'
                  }
              }
        }

        stage('AntBuild13') {
          steps {
            bat 'mvn ant:ant'
            withAnt(installation: 'Default') {
              bat 'ant compile'
            }

          }
        }


      }
    }

  }
}