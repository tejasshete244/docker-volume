pipe {
        agent {
           label {
                   label 'built-in'
                   customWorkspace '/mnt/docker2/'
                 }
             }

 stages {
       stage ('docker-volume'){
               steps {
                   sh "docker volume create vol1"
                   }
               }
       stage ('git-clone'){
               steps {
                  dir('/var/lib/docker/volumes/vol1/_data/'){
                   sh "git clone https://github.com/tejasshete244/docker-volume.git -b master"
                    
                   }
               }
          }
        stage ('docker-run'){
                  steps {
                     sh "docker run -itdp 80:80 --name 22Q1 -v vol1:/usr/local/apache2/htdocs httpd"

                      }
                      
                   }    

              }
       
         }
