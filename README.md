# maven-updated-installation


#!/bin/sh
echo Have you created a RedHat AWS server that has 4gb RAM or more? Enter 1 for yes and 2 for no.
read response
if
        (( $response == 1 ))
then
        echo Excellent! Your installations will resume shortly...
        sleep 1
        sudo hostname maven
        cd /opt
        echo Installing apps to get us running...
        sudo yum install wget vim nano tree unzip git-all -y
        echo Installing java...
        sudo yum install java-11-openjdk-devel java-1.8.0-openjdk-devel -y
        sleep 1
        java -version
        sleep 1
        git --version
        sleep 1
        echo Maven software installation will start in a moment...
        sleep 1
        sudo wget https://dlcdn.apache.org/maven/maven-3/3.8.5/binaries/apache-maven-3.8.5-bin.zip
        echo Unzipping to start in a moment...
        sleep 1
        sudo unzip apache-maven-3.8.5-bin.zip
        echo Deleting the zip file...
        sleep 1
        sudo rm -rf apache-maven-3.8.5-bin.zip
        echo Renaming the installation directory...
        sleep 1
        sudo mv apache-maven-3.8.5/ maven
        echo Setting Environmental Variable for $whoami ...
        echo "export M2_HOME=/opt/maven"   >>  ~/.bash_profile
        echo "export PATH=$PATH:$M2_HOME/bin"   >> ~/.bash_profile
        sleep 1
        echo Refreshing the .bash_profile file...
        sleep 1
        source ~/.bash_profile
else
        echo You will need to set up an AWS server with a minimum of 4GB RAM.
fi
