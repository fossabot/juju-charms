Juju Charms for RestComm Components

# Deploying/Starting Juju
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bhttps%3A%2F%2Fgithub.com%2FRestComm%2Fjuju-charms.svg?type=shield)](https://app.fossa.io/projects/git%2Bhttps%3A%2F%2Fgithub.com%2FRestComm%2Fjuju-charms?ref=badge_shield)



    #boostrap Juju environment
    juju bootstrap
    #get logs
    juju debug-log
    # deploy juju gui
    juju deploy juju-gui
    #expose juju-gui for public access
    juju expose juju-gui
    
### juju-quickstart option
If you have juju-quickstart https://launchpad.net/juju-quickstart to deploy and connect to juju GUI use this one command for current bootstrapped envrioment. See also: https://github.com/juju/cheatsheet

    juju-quickstart     


#Deploying RestComm
There is now 2 options for deploying RestComm :

##1. Automated way - All Integrated Bundle
Import https://jujucharms.com/u/jean-deruelle/mobicents-restcomm-mysql-bundle/ through the Juju GUI that you just deployed previously

##2. Manual way - Deploying MySQL and RestComm Charms
Download this project
For using local deployment by example

    git clone https://github.com/RestComm/juju-charms.git
    
    #deploy backend DB
    juju deploy mysql
    #if you use juju local (ie lxc - https://jujucharms.com/docs/stable/config-local) as environment mysql needs this below
    #juju set mysql dataset-size='512M'
    #juju resolved -r mysql/#
    #deploy RestComm Unit (the same folder where you issued git clone command)
    juju deploy -u --repository=juju-charms/mobicents-restcomm-charm/ local:trusty/mobicents-restcomm 
    #connect RestComm to the backend DB
    juju add-relation mobicents-restcomm mysql
    juju expose mobicents-restcomm


#Test RestComm Charm

Go to http://&lt;public_ip&gt;:8080  (username: administrator@company.com, password: RestComm) for Admininstration

## WebRTC call

Go to http://&lt;public_ip&gt;:8080/olympus for WebRTC P2P Live Video chat

Please refer to this link: http://caniuse.com/#search=webrtc  for the most up-to-date information about browser WebRTC support.

## Clean enviroment  
When you done, you can clean ennviroment and destroy all services (do not terminate machines). 

    juju-deployer -D 


## License
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bhttps%3A%2F%2Fgithub.com%2FRestComm%2Fjuju-charms.svg?type=large)](https://app.fossa.io/projects/git%2Bhttps%3A%2F%2Fgithub.com%2FRestComm%2Fjuju-charms?ref=badge_large)