pipeline {
        agent {
           label {
                   label 'built-in'
                   customWorkspace '/mnt/docker2/'
                 }
             }

 stages {
       stage ('docker-volume'){
               steps {
                   sh "docker volume rm vol1"
                   sh "docker volume create vol1"
                   }
               }
       stage ('git-clone'){
               steps {
                   sh "git clone https://github.com/tejasshete244/docker-volume.git -b master"
                   sh "cp -r /mnt/docker2/docker-volume/index.html /var/lib/docker/volumes/vol1/_data/"
                    
                 }
          }
        stage ('docker-run'){
                  steps {
                     sh "docker stop 22Q1"
                     sh "docker container rm 22Q1"
                     sh "docker run -itdp 80:80 --name 22Q1 -v vol1:/usr/local/apache2/htdocs httpd"

                      }
                      
                   }    

              }
       
         }
