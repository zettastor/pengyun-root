1. clone code from github repository:

git clone git@server7:main/pengyun-main.git

cd pengyun-main/

git submodule init

//pull all codes from each submodule

git submodule update

// Switch branches of all submodule to their master branches

git submodule foreach git checkout master

//pull all codes again to ensure we get the latest codes

git submodule foreach git pull

2. Build the project

 mvn clean install 

 or if there are errors with the unit tests

 mvn clean install -DskipTests

 (if there are errors asking for 'pengyun-datanode', comment out the line with 'pengyun-datanode' in pengyun-main/pom.xml)
 
 note: when you need update pengyun-dnmodel-2.3.0.jar or pengyun-datanode_service-2.3.0.jar and compile the submodules of pengyun-datanode and pengyun-datanode_core, you cannot input "mvn clean install" with current directory of pengyun-main in terminal, you should follow as:
11. copy the packages of pengyun-dnmodel-2.3.0.jar and pengyun-datanode_service-2.3.0.jar to the directory of pengyun-datanode_binary/src/main/resources , then mvn clean install in this submodule;
 2. compile dependencies of pengyun-datanode_core one by one, then compile pengyun-datanode_core
 3. compile pengyun-datanode 
 4. copy this new packages of pengyun-datanode_core-2.3.0.jar and pengyun-datanode-2.3.0-internal.tar.gz to the directory of pengyun-datanode_binary/src/main/resources
 5. now you can input "mvn clean install" with current directory of pengyun-main

3. Run the application:

sudo bin/LaunchTestStation

Note this script can wipe out all existing executable codes and recreate new ones. Also it launches all services and create a volume for testing. This script has lots of options which can be referred from its source code. When it completes the execution, it will prints out volume id which can be used to do testing. 


4. Run the console

There is a console which can be used to manage the pengyun storage. The console is one of submodules under pengyun-main. 


