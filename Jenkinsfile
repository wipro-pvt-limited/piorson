def version ="${env.BUILD_ID}"

pipeline{

agent any

tools{
    
    maven "maven3.8.3"
    
} // tools

/*
 options{
 
    timestamps()

    properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')

 } */ //closing options

/* triggers{

    pollSCM('* * * * *')
    
 } */ //closing triggers
 
 
stages{

stage('CheckoutCode'){

steps{
git branch: 'main', credentialsId: '28f70f33-2db1-46d0-94b8-f0fe4523e251', url: 'https://github.com/wipro-pvt-limited/piorson.git'
}

}

stage('Build'){

steps{

sh "mvn clean package"

}
}

stage('docker image build'){
    
    steps{
        
        sh """\
        
        
          #!/bin/bash -l

        
        docker build -t swamykishore:${version} .
        
        """
        
    }
}

stage('Docker login'){
    
    steps{
        
        sh """\
          #!/bin/bash -l

        docker login -u shaikfayazz444 -p 8688949515
        
        docker tag swamykishore:${version} shaikfayazz444/ayaan:${version}
        
        """
        
    }
    
    
}


stage('docker push'){
    
    steps{
        
        sh """\
        #!/bin/bash -l
       docker push shaikfayazz444/ayaan:${version}
        
        """
        
    }
}

}//stages closing
}//pipeline closing

/*post{
    
    success{
        
    }
    
    
} */

