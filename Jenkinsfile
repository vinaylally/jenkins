node('built-in') 
{



stage('continuous download') 
{
    
    git 'https://github.com/vinaylally/jenkins.git'    
}

stage('continuous build') 
{
    
    sh 'mvn package'
    
}  

 stage('continuoos deploy') 
{
    
  deploy adapters: [tomcat9(credentialsId: 'iqiq', path: '', url: 'http://172.31.31.30:8080')], contextPath: 'qa', war: '**/*.war'  
    
}   
stage('continuous test') 
{
    
  git 'https://github.com/selenium-saikrishna/FunctionalTesting.git'
  sh 'java -jar /var/lib/jenkins/workspace/scriptedpipeline/testing.jar'
    
}
stage('continuous delivaery') 
{
input message: 'need approval from dm', submitter: 'lally'  
deploy adapters: [tomcat9(credentialsId: 'da4a7826-ff67-4ed4-9149-ddb0a9c0349f', path: '', url: 'http://172.31.26.209:8080')], contextPath: 'prod', war: '**/*.war'
    
}
    
}
