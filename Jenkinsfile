pipeline {
    agent any
    
       
    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "maven"
    }
    
     environment { 
            mybranch = env('BRANCH_NAME') 
    }


    stages {

         stage ('branch name') {
            steps {
                    echo $mybranch
            }
        }
        
        stage ('Compile Stage') {
            when {
                
                   expression {
                       return env.BRANCH_NAME == 'dev';}
          
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
