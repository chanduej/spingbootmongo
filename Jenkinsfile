node{ 
    stage('SCM Checkout')
    {
        git credentialsId: 'GIT_CREDENTIALS', url:  'https://github.com/chanduej/spingbootmongo.git',branch: 'master'
    }
    stage(" Maven Clean Package")
    {
      def mavenHome =  tool name: "maven3", type: "maven"
      def mavenCMD = "${mavenHome}/bin/mvn"
      sh "${mavenCMD} clean package"
      
    }
    stage('Build Docker Image')
    {
        sh 'docker build -t lucky0524/spring-boot-app .'
    }
    stage('Push Docker Image')
    {
        withCredentials([string(credentialsId: '', variable: 'dockerhubcredentials')])
        {
             sh "docker login -u lucky0524 -p ${dockerhubcredentials}"
        }
        sh 'docker push lucky0524/spring-boot-app'
    } 
 }
