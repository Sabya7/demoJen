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

            always {
              junit '/target/**/*.xml'
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

    stage('mail') {
      steps {
        input(message: 'Want to Mail', submitter: '"Sabya"', submitterParameter: 'Hello')
        script {
          env.MailID = input message: 'Want To Mail?',
          parameters: [string(defaultValue: 'sabyasachisahoo62.ss@gmail.com', description: '{mailid}', name: 'MailID', trim: true)], submitter: '"Sabya"', id: 'mailer'
        }

        echo "${env.MailID}"
        mail(subject: 'BuildRes', body: 'hrlllllllllllllllllo', to: "${env.MailID}")
      }
    }

    stage('sonar_scan') {
      steps {
        withSonarQubeEnv('sonar_server') {
          bat 'mvn sonar:sonar'
        }

      }
    }

    stage('quality_gate') {
      steps {
        sleep(time:60,unit:"SECONDS")
        waitForQualityGate()
      }
    }

  }
}
