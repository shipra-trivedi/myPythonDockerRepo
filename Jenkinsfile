node {
    def mvnHome = tool 'Maven'
    registryName = "testimage"
    registryUrl = "myakacrregistry.azurecr.io"
    registryCredential= "ACR"
    
    
    stage('checkout'){
        echo "Into Checkout"
        //checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Sujana-Suresh/myPythonDockerRepo.git']]])
         checkout scm
          }
    
    stage('Build'){
        echo "Into Build"
        sh "${mvnHome}/bin/mvn clean install -f pom.xml"
          }
    
    stage ('Build Docker image'){
        echo "Into buiding docker image"
        docker.build registryName
          }
          
    //stage('Tagging') {
        //sh "az acr login -n myakacrregistry --username myakacrregistry --password tlQv=XzxYOf/Ix8+tZj/Uj3lFelycVjG"
        //sh "sudo docker tag testimage myakacrregistry.azurecr.io/testimage:latest"
        //sh "sudo docker push myakacrregistry.azurecr.io/testimage:latest"
         // }

    stage('AKS deploy'){
        sh 'sudo az aks install-cli'
        sh 'kubectl apply -f k8s-spring-boot-deployment.yml'

    }
    }
