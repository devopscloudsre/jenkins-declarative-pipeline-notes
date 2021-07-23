pipeline {
    agent any
    
       
    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "maven"
    }

    stages {
        stage ('Compile Stage') {

            when {
                 branch 'dev'             
              }

            steps {
                    sh 'mvn clean package'
            }
        }

        stage ('Testing Stage') {
             when {
                  branch 'release'             
              }
            
            steps {
              
                    sh 'mvn test'
          
            }
        }


        stage ('Install Stage') {
            when {
                  branch 'main'             
              }
            
            steps {
              
                    sh 'mvn install'
             
            }
        }
    }
}
