pipeline{
  agent{
    node {label 'slave'}
  }
  stages{
    stage('clone repo'){
      steps{
        script{
          git 'https://github.com/CodeGitti/demo-java.git'
          sh 'echo "Clone completed"'
          sh 'pwd'
        }
      }
    }
    stage('Build the project'){
      steps{
        script{
          sh 'mvn clean package'
          sh 'echo "build complete"'
        }
      }
    }
    stage('deploy to tomcat'){
      steps{
        script{
          sh 'echo "Deploy started"'
          sh 'sudo cp /home/jenkins/jenkins_slave/workspace/pipeline1/target/demo.war /home/ubuntu/apache-tomcat-9.0.87/webapps/'
          sh 'sudo /home/ubuntu/apache-tomcat-9.0.87/bin/shutdown.sh'
          sh 'sleep 6'
          sh 'sudo /home/ubuntu/apache-tomcat-9.0.87/bin/startup.sh'
          sh 'echo "Completed"'
        }
      }
    }
  }
}
