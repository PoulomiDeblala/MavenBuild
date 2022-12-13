pipeline{
     triggers {
    githubPush()
  }
agent any
stages(‘CI CD Pipeline’){
  stage(‘Code Checkout’){
    steps{
        script{
            git credentialsId: ‘0dbfbc4e-5328-4dfb-9127-2ad8a97c34af’, url: ‘https://github.com/PoulomiDeblala/MavenBuild.git’
            }
        }
    }
 
  stage(‘Build’){
    steps{
        script{
            sh “mvn clean install -Dmaven.test.skip=true”
        }
    }  
  }
  stage(‘Test’){
    steps{
        script{
            sh “mvn clean org.jacoco:jacoco-maven-plugin:prepare-agent install -Pcoverage-per-test”
        }
    }  
  }
  stage(‘Notification’){
    steps{
        script{
           emailext body: ‘Build is successful’, subject: ‘Build Email’, to: ‘polo161996@gmail.com’
        }
    }  
  }
}
}
