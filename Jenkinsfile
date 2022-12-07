pipeline{
    agent any
   environment {
       dockerHub = credentials('dockerCredentID') // Secret value is 'sec%ret'
    }
   tools {
        maven "maven" // You need to add a maven with name "3.6.0" in the Global Tools Configuration page
    }
    stages{
        stage('git checkout'){
            steps{
                 git credentialsId:'credentID',url:'https://github.com/juvetus/devops-automation'
            }
        }
        stage('Build the application'){
            steps{
                bat' mvn clean install'
            }
        }
        stage('Unit Test Execution'){
            steps{
                 bat 'mvn test'
            }
        }
      stage('Build the image docker'){
          steps{
              bat 'docker build -t sylviane/devops-automation .'
          }
      }
      stage('Build the image dockerHub'){
          steps{
              //bat 'echo $dockerHub_PSW | docker login -u $dockerHub_USR --password-stdin'
              //withCredentials([string(credentialsId: 'dockerCredentID', variable: 'userVariable')]) {
            // some block
            //bat "dockerlogin-Sylviane-p$userVariable"
            withCredentials([string(credentialsId: 'userId', variable: 'userVariable')]) {
    // some block
    bat 'docker login -u sylviane -p %userVariable%'
}
            
              bat 'docker build -t sylviane/devops-automation .'
          }
      }
    }
}
