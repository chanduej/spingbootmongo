node{
     
    stage('SCM Checkout'){
        git credentialsId: 'GIT_CREDENTIALS', url:  'https://github.com/chanduej/spingbootmongo.git',branch: 'master'
    }
    
    stage(" Maven Clean Package"){
      def mavenHome =  tool name: "maven3", type: "maven"
      def mavenCMD = "${mavenHome}/bin/mvn"
      sh "${mavenCMD} clean package"
      
    } 
 }
