pipeline {
  agent any
  stages {
    stage('Build13') {
      parallel {
        stage('Build13') {

          steps {
            echo 'Hello Sabya'
            bat 'mvn clean compile package -DskipTests'
          }

          post {
                  success {
                      archiveArtifacts artifacts: '/target/*.*', fingerprint: true

                  }
                  always {
                              junit '/target/**/*.xml'
                          }
              }

        }

        stage('AntBuild13') {
          steps {
            bat 'mvn ant:ant'
            withAnt(installation: 'Default') {
              bat 'ant compile jar'
            }

          }
          post {
                success {
                                archiveArtifacts artifacts: '/target/*.*', fingerprint: true

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
            //bat 'set'
            mail(subject: 'BuildRes', body: 'hrlllllllllllllllllo', to: "${env.MailID}")
          }
    }

  }
}