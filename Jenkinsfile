pipeline {
  agent any

  environment {
    DISCORD_WEBHOOK = 'https://discord.com/api/webhooks/1386880803652243487/sNxHJ6Y9OXVdMg5tWjjrA7c6Ls7v6LInQXS2I9da7GTIGoj79QODpjfnYbqmkIDpDCEQ'
  }

  stages {
    stage('Notificar Discord: Subindo maquinas') {
      steps {
        sh '''
          curl -H "Content-Type: application/json" -X POST -d '{"content": "Novo push na branch ${env.GIT_BRANCH} (Build #'"${BUILD_NUMBER}"')."}' ${DISCORD_WEBHOOK}
        '''
      }
    }

    stage('echo') {
      steps {
        echo "FOIIIIIIIIIIIIIIIIIIII"
      }
    }
  }

  post {
    success {
      sh '''
        curl -H "Content-Type: application/json" -X POST -d '{"content": "Push na branch ${env.GIT_BRANCH} realizado com successo (Build #'"${BUILD_NUMBER}"')."}' ${DISCORD_WEBHOOK}
      '''
    }
    failure {
      sh '''
        curl -H "Content-Type: application/json" -X POST -d '{"content": "❌ Falha (Build #'"${BUILD_NUMBER}"'). Verifique o Jenkins."}' ${DISCORD_WEBHOOK}
      '''
    }
  }
}

