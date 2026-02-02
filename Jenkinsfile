pipeline {
    agent any

    /* 
       triggers: GitHub이나 Gitea의 Webhook 신호를 받기 위한 설정입니다. 
       GitHub 환경에서는 'githubPush()'가 활성화되어야 합니다.
    */
    triggers {
        githubPush() // GitHub Webhook 연동 시 필수
        pollSCM('')  // SCM 변화 감지 활성화
    }

    stages {
        stage('Checkout') {
            steps {
                // Jenkins Pipeline에서 SCM 설정이 되어있다면 자동으로 체크아웃을 수행합니다.
                checkout scm
            }
        }

        stage('Build') {
            steps {
		sh 'scripts/build.sh'
                // 기존 config.xml의 <command>echo hello</command> 부분을 수행합니다.
                script {
                    sh 'echo "hello"'
                    echo "Current Branch: ${env.BRANCH_NAME ?: 'main'}"
                }
            }
        }
    }

    post {
        success {
            echo 'Build and Deployment completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Please check the logs.'
        }
    }
}
