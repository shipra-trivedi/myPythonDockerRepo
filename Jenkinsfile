node {
    def mvnHome = tool 'Maven'
    registryName = "mysampleimage"
    registryUrl = "myakacrregistry.azurecr.io"
    registryCredential= "ACR"
    
    
    stage('checkout'){
        echo "Into Checkout"
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Sujana-Suresh/myPythonDockerRepo.git']]])
          }
    
    stage('Build'){
        echo "Into Build"
        sh "${mvnHome}/bin/mvn clean install -f pom.xml"
          }
    
    stage ('Build Docker image'){
        echo "Into buiding docker image"
        docker.build registryName
          }
          
    stage('Tagging') {
        sh "az acr login -n myakacrregistry --username myakacrregistry --password tlQv=XzxYOf/Ix8+tZj/Uj3lFelycVjG"
        //sh "sudo docker tag mysampleimage myakacrregistry.azurecr.io/mysampleimage"
          }
    }
