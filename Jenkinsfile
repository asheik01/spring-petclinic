 pipeline {
    agent any
 triggers { pollSCM('*/3 * * * * ') }   
    
    stages {
        stage('Git Clone') {
            steps {
               git branch: 'main', url: 'https://github.com/asheik01/spring-petclinic.git'
            }
        }
        stage('Building Code'){
            steps{
                sh './mvnw package'
            }
        }
        stage('downloading artifacts'){
            steps{archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false}
        }
    }
   stage('unit test results') {
    steps
            junit 'target/surefire-reports/*.xml'
   }
        
        }
}   