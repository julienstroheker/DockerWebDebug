node {
   stage('Preparation') { // for display purposes
      // Get some code from a GitHub repository
      git url: 'https://github.com/julienstroheker/DockerWebDebug.git', branch: 'green'
   }
   stage('Build') {
      sh 'docker build -t julienstroheker/web-debug:green .'
   }
   stage('Push') 
   withCredentials([[$class: 'UsernamePasswordMultiBinding', credentialsId: 'dockerhub',
                    usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD']])
   {
      sh 'docker login --username=$USERNAME --password=$PASSWORD' 
      sh 'docker push julienstroheker/web-debug:green'
   }
}