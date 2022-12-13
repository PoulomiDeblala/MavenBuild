pipeline{
     triggers {
    githubPush()
  }
agent any
stages(‘CI CD Pipeline’){
  stage(‘Code Checkout’){
    steps{
        script{
            git credentialsId: ‘0a1544c3-a902-4811-a373-c8ae9f018d9e’, url: ‘https://github.com/PoulomiDeblala/MavenBuild.git’
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
