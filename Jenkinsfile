pipeline {
  agent {
    docker {
      image 'maven:3.6.3-jdk-11-slim'
    }

  }
  stages {
    stage('build') {
      steps {
        echo 'compiling the code'
        sh 'mvn compile'
      }
    }

    stage('test') {
      steps {
        echo 'running the unit test'
        sh 'mvn clean test'
      }
    }

    stage('package') {
      steps {
        echo 'generating artifacts'
        sh 'mvn package -DskipTests'
        archiveArtifacts 'target/*.war'
      }
    }

  }
  post {
    always {
      echo 'This pipeline is completed..'
    }

  }
}
