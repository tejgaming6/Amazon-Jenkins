pipeline {
    agent any
    environment {
        // Use PATH+EXTRA to append to PATH properly
        PATH = "/usr/bin:/bin:/opt/homebrew/bin"
    }
    stages {

        stage('pull') {
            steps {
                git branch: 'main', url: 'https://github.com/PraveenKuber/Amazon-Jenkins.git'
            }
        }

         stage('validate') {
            steps {
                sh 'mvn validate'
            }
        }
        
        stage('compile') {
            steps {
                sh 'mvn compile'
            }
        }

         stage('test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('build') {
            steps {
                 sh 'mvn clean install'
            }
        }

        
    }

  post{

       always{
       echo 'clean stuff'
   }
  success{
     echo 'Build success'
  }
    
  unstable{
       echo 'check with qa team'
   }
   failure{
       echo 'Failure in the build'
   }
    aborted{
       echo 'manually stopped by the user'
   }

  }


}
