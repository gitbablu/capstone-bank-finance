pipeline{
    agent any
    stages{
        stage('checkout the code from github'){
            steps{
                 git url: 'https://github.com/gitbablu/capstone-bank-finance.git'
                 echo 'github url checkout'
            }
        }
     //   stage('codecompile'){
            steps{
                echo 'starting compiling'
                sh 'mvn compile'
            }
        }
        stage('codetesting'){
            steps{
                sh 'mvn test'
            }
        }
        stage('qa'){
            steps{
                sh 'mvn checkstyle:checkstyle'
            }
        }
        stage('building package'){
            steps{
                sh 'mvn package'
            }
        } //
        stage('run dockerfile and build a image'){
          steps{
               sh 'docker build -t bank-finance .'
           }
         }
        stage('run image and acess the app on port expose 8091'){
            steps{
                sh 'docker run -dt -p 8091:8091 --name c01 bank-finance'            }
        }   
    }
}
