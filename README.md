# Setup for mongo under OSX

Clone this repo, or get the example config.

    git clone https://daneroo@github.com/daneroo/setup-osx-mongo.git mongo

Download the [latest binary for OSX](http://www.mongodb.org/downloads). 
As of this writing this was:

    curl http://fastdl.mongodb.org/osx/mongodb-osx-x86_64-1.8.1.tgz > mongo.tgz
    tar xzf mongo.tgz
    # rm mongo.tgz  # remove this when you're done
    # link or move the bin directory
    #ln -s mongodb-osx-x86_64-1.8.1/bin bin
    mv mongodb-osx-x86_64-1.8.1/bin .
    
    # dirs to hold data and logs
    mkdir data
    mkdir logs

## Run server from command-line
    bin/mongod --dbpath ./data
    
## Command line client
To run the client (console):

   bin/mongo
   
   # you may want to add `bin` to you PATH environment variable, in your `~/.profile`
   export MONGO_HOME=~/Downloads/mongo/bin
   export PATH=$PATH:$MONGO_HOME/bin
    
## Install as daemon
This uses launchctl to start the mongo daemon.

I put my installation into ~/Downloads/mongo, but you can put your anywhere.
be sure to reflect you changes in your launchctl config file, then copy and load the config.

    cp org.mongodb.mongod.plist ~/Library/LaunchAgents/org.mongodb.mongod.plist
    launchctl load ~/Library/LaunchAgents/org.mongodb.mongod.plist
    # if you nee to load again unload it first:
    launchctl unload ~/Library/LaunchAgents/org.mongodb.mongod.plist

To start and stop the service:
    
    launchctl start org.mongodb.mongod
    launchctl stop org.mongodb.mongod
