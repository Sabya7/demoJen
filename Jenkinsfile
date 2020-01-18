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
            bat 'mvn clean compile package -DskipTests'
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

    stage('mail') {
      steps {
        input(message: 'Want to Mail', submitter: '"Sabya"', submitterParameter: 'Hello')
        input(message: 'Want To Mail?', parameters: [string(defaultValue: 'sabyasachisahoo62.ss@gmail.com', description: '{mailid}', name: 'MailID', trim: true)], submitter: '"Sabya"', id: 'mailer')
        mail(subject: 'BuildRes', body: 'hrlllllllllllllllllo', to: env.mailer.MailID)
      }
    }

  }
}