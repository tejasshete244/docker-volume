pipeline {
        agent {
           label {
                   label 'built-in'
                   customWorkspace '/mnt/docker2/2/'
                 }
             }

 stages {
       stage ('docker-volume'){
               steps {
                   sh "docker stop 22Q2"
                   sh "docker container rm 22Q2"
                   sh "docker volume rm vol2"
                   sh "docker volume create vol2"
                   }
               }
       stage ('git-clone'){
               steps {
                   sh "rm -rf *"
                   sh "git clone https://github.com/tejasshete244/docker-volume.git -b 22Q2"
                   sh "cp -r /mnt/docker2/2/docker-volume/index.html /var/lib/docker/volumes/vol2/_data/"
                   sh "chmod -R 777 /var/lib/docker/volumes/vol2/_data/"
                    
                 }
          }
        stage ('docker-run'){
                  steps {
                   sh "docker run -itdp 90:80 --name 22Q2 -v vol2:/usr/local/apache2/htdocs httpd"

                      }
                      
                   }    

              }
       
         }
