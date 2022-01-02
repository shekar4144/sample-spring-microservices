pipeline {
agent {
label 'Build-server'
}

stages {

stage ('Checkout') 
{
steps
    {
    
        checkout scm
        
    }
    
}
stage ('Build') 
{
    steps
    {
       sh "cd /home/ubuntu/workspace/devops8th/account-service ; mvn clean install " 
    }
}

   
stage ('dockerimageBuild')
    {
    steps
    {
        sh "cd /home/ubuntu/workspace/devops8th/account-service; sudo docker build -t account-service . " 
    }
}
     stage ('dockerimagepush ') 
{
    steps
    {
       sh "cd /home/ubuntu/workspace/devops8th/account-service ; sudo  docker login -rajashekar414 -Shekar@123 "
        sh "cd /home/ubuntu/workspace/devops8th/account-service ; sudo docker tag account-service rajashekar414/account-service "
        sh "cd /home/ubuntu/workspace/devops8th/account-service ; sudo docker push rajashekar414/account-service  "
        
        
    }
}
    
    
stage ('kubernetes') 
    {
        steps {
            node (' Ansible-server') {
             sh " sudo ansible-playbook /root/k8s.yaml"
   
    }
}
}
}
    
    
}
