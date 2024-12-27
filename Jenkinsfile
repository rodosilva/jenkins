pipeline {
  // Lugar donde se va a ejecutar el pipeline
  // agent { label 'agente1' }
  agent any // Ejecutar en el Agente que tenga disponible
  
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

    stage('Deploy') {
      when {
        step 'success' //branch 'qa'
      }
      steps {
        sshagent(credentials: ['Credentials ID']) {
        sh './deploy.sh'
        }
      }
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

}