# DockerLab

<p>
  
    mkdir DockerLab
    nano DockerLab/DockerFile
    cd DockerLab
  
  <h6>
    
            FROM ubuntu:bionic



            RUN mkdir Test
            RUN mkdir -p Test/usr/local/bin
            COPY script1.bash Test/usr/local/bin/test.bash

            RUN chmod u+x Test/usr/local/bin/test.bash

            RUN mkdir Test/DEBIAN
            COPY control Test/DEBIAN/control

            #RUN find ./ -type f ! -regex '.*?DEBIAN.*' -exec md5sum {} \; > Test/DEBIAN/md5sums
            RUN dpkg-deb -Zgzip --build Test

    
    
   </h6>
 </p>
 
 
 
 <p>
         
    nano script1.bash
  
       <h6>  
             #!bin/bash

            printName () {
                    DATE=`date +%d-%m-%y`
                    echo "$1 $DATE" > ekmek.txt
            }
         
            printName Burak
         
      </h6>
             
    chmod u+x script1.bash         
     
     nano control
     
      <h6>
      
              Package: Test
              Version: 1.0
              Maintainer: Burak
              Date: 12-15-2021
              Architecture: amd64
              Description: a dummy develops app

    </h6>

    docker build -t dockerfile . 
    docker run -it dockerfile bash
    
    
    sudo docker cp 532d9968f085:Test.deb /home
  
  
    
</p>
