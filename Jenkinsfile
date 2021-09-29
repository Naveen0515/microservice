pipeline {
agent {
label 'akhila123'
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
       sh "cd /home/ubuntu/workspace/akhila123/account-service ; mvn clean install " 
    }
}

   
stage ('dockerimageBuild')
    {
    steps
    {
        sh "cd /home/ubuntu/workspace/devops28thsep/account-service; sudo docker build -t account-service . " 
    }
}
     stage ('dockerimagepush ') 
{
    steps
    {
       sh "cd /home/ubuntu/workspace/akhila123/account-service ; sudo  docker login -unaveen0515 -pNaveen@515 "
        sh "cd /home/ubuntu/workspace/akhila123/account-service ; sudo docker tag account-service naveen0515/account-service "
        sh "cd /home/ubuntu/workspace/akhila123/account-service ; sudo docker push naveen0515/account-service  "
        
        
    }
}
    
    
stage ('k8sdeployment') 
    {
        steps {
            node (' Ansible-server') {
             sh " sudo ansible-playbook /root/k8s.yaml"
   
    }
}
}
}
    
    
}
