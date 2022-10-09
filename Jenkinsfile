pipeline {
        agent {
           label {
                   label 'built-in'
                   customWorkspace '/mnt/docker2/3/'
                 }
             }

 stages {
       stage ('docker-volume'){
               steps {
                   sh "docker stop 22Q3"
                   sh "docker container rm 22Q3"
                   sh "docker volume rm vol3"
                   sh "docker volume create vol3"
                   }
               }
       stage ('git-clone'){
               steps {
                   sh "rm -rf *"
                   sh "git clone https://github.com/tejasshete244/docker-volume.git -b 22Q3"
                   sh "cp -r /mnt/docker2/3/docker-volume/index.html /var/lib/docker/volumes/vol3/_data/"
                   sh "chmod -R 777 /var/lib/docker/volumes/vol3/_data/"
                    
                 }
          }
        stage ('docker-run'){
                  steps {
                   sh "docker run -itdp 70:80 --name 22Q3 -v vol3:/usr/local/apache2/htdocs httpd"

                      }
                      
                   }    

              }
       
         }
