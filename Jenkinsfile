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
        sleep 3
      }
    }

  }
  tools {
    maven 'MAVEN_3_8_6'
    jdk 'JDK_11'
  }
}