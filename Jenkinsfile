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
          sh 'sudo cp /var/lib/jenkins/workspace/pipeline1/target/demo.war /home/ubuntu/apache-tomcat-10.1.19/webapps/'
          sh 'sudo /home/ubuntu/apache-tomcat-10.1.19/bin/shutdown.sh'
          sh 'sleep 5'
          sh 'sudo /home/ubuntu/apache-tomcat-10.1.19/bin/startup.sh'
          sh 'echo "Completed"'
        }
      }
    }
  }
}
