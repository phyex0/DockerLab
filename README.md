# DockerLab
Creating a container in docker and creating a package in the docker then Copying into local directory

<p>
  
    mkdir DockerLab
    nano DockerLab/DockerFile
  
  <h6>
    
          FROM ubuntu:bionic



          RUN mkdir Test
          RUN mkdir -p Test/usr/local/bin
          RUN echo """

          #!/bin/bash

          print () {
                  DATE=`date +%d-%m-%y`
                  echo "$1 $DATE" > ekmek.txt

          }

          print Burak

          """ > Test/usr/local/bin/test.bash

          RUN chmod u+x Test/usr/bin/test.bash
          RUN mkdir Test/DEBIAN
          RUN echo """
          Package: test
          Version: 1.0
          Date: 2021-12-15 14:24:00
          Architecture: amd64
          Maintainer: Burak
          Description: a dummy developer develops a test

          """ > Test/DEBIAN/control

          RUN find ./ -type f ! -regex '.*?DEBIAN.*' -exec md5sum {} \; > Test/DEBIAN/md5sums
          RUN dpkg-deb -Zgzip --build Test
    
    
  </h6>
    
</p>
