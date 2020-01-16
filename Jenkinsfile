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
        }

        stage('AntBuild13') {
          steps {
            bat 'mvn ant:ant'
            bat 'set PATH=%ANT_HOME%\\bin;'
          }
        }

      }
    }

    stage('antCompile') {
      steps {
        bat 'set PATH=%ANT_HOME%\\bin;'
        bat 'ant compile'
      }
    }

  }
}