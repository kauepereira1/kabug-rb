pipeline {
    agent {
        docker {
            image 'qaninja/rubywd'
        }
    } 
    
    stages {
        stage('Build'){
            steps {
                echo 'Building or Resolve Dependencies'
                sh 'bundle install'
            }
        }
        stage('Test'){
            steps{
                echo 'Running regression tests'
                 sh 'bundle exec cucumber -p ci'
            }
        }
        stage('UAT'){
            steps{
                echo 'Wait for User Acceptance' 
                input(message: 'Go to prodution?', ok: 'Yes')
            }
        }
        stage('Prod'){
            steps{
                echo 'WebApp in Ready :)'
            }
        }
    }
}