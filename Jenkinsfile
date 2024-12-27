pipeline {
  // Lugar donde se va a ejecutar el pipeline
  agent any
  
  // Los estados o bloques
  stages {
    stage('Vertificar Docker') {
      steps {
        sh 'docker info'
      }
    }

    stage('Docker build') {
      steps {
        sh 'docker build -t jenkins-laravel .'
      }
    }
    
    // Correr los Tests Propios de Laravel
    stage('Run test') {
      steps {
        sh 'docker run --rm jenkins-laravel ./vendor/bin/phpunit tests'
      }
    }

    post {
      success {
        slackSend(channel: '#devops', message: "Todo bien")
      }
      
      failure {
        slackSend(channel: '#devops', message: "Algo anda mal")
      }
    }

    //stage('Sonarqube') {
    //  steps {
    //    script {
    //      docker.image('sonarsource/sonar-scanner-cli').inside('--network ci-network') {
    //        sh 'sonar-scanner'
    //      }
    //    }
    //  }
    //}

    // stage('Deploy') {
    //   steps {
    //     sshagent(credentials: ['71a7ee52-1c6a-476a-860f-6070ab4eb875']) {
    //       sh './deploy.sh'
    //     }
    //   }
    // }
  }
}