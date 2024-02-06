pipeline {
  agent any
  stages {
    stage('Compilar') {
      parallel {
        stage('Compilar') {
          steps {
            bat 'mvn -v'
            bat 'mvn clean package'
          }
        }

        stage('Etapa compilar paralelo') {
          steps {
            timestamps() {
              echo 'Hola etapa compilar paralelo'
              sleep 3
            }

          }
        }

      }
    }

    stage('Etapa Fin') {
      steps {
        echo 'Etapa Fin'
        archiveArtifacts '**/*'
        sleep 3
      }
    }

    stage('Ejecución') {
      steps {
        bat 'mvn exec:java -Dexec.mainClass=com.curso.Principal'
      }
    }

  }
  tools {
    maven 'MAVEN_3_8_6'
    jdk 'JDK_11'
  }
  post {
    always {
      cleanWs()
      dir("${env.WORKSPACE}@tmp") {
        deleteDir()
      }

      dir("${env.WORKSPACE}@script") {
        deleteDir()
      }

    }

  }
}