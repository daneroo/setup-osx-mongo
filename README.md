## Setup for mongo under OSX

Clone this repo, or get the example config.

    git clone https://daneroo@github.com/daneroo/setup-osx-mongo.git mongo

Download the [latest binary for OSX](http://www.mongodb.org/downloads). 
As of this writing this was:

    curl http://fastdl.mongodb.org/osx/mongodb-osx-x86_64-1.8.1.tgz > mongo.tgz
    tar xzf mongo.tgz
    # rm mongo.tgz  # remove this when you're done
    # link or move the bin directory
    ln -s mongodb-osx-x86_64-1.8.1/bin bin

# Run from command-line
  bin/
# Install as daemon
This uses launchctl to start the mongo daemon.

I put my installation into ~/Downloads/mongo, but you can put your anywhere.
be sure to reflect you changes in your launchctl config file

    cp org.mongodb.mongod.plist ~/Library/LaunchAgents/org.mongodb.mongod.plist
