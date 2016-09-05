Cannot log in to Archer without entering passphrase
===================================================

Also, ssh-add doesn't work: 

    ssh-add
    => Error connecting to agent: No such file or directory

See [recommended way to fix problem](http://cms.ncas.ac.uk/wiki/FAQ_T4_F5). N.B.
I haven't tried this yet.

Or (worked for me 5/9/16):

Try restarting the ssh-agent:

    ps -flu markmuetz|grep ssh-agent
    kill <proc_id> 

or 

    killall -u markmuetz ssh-agent

then:
    
    . .ssh/ssh-setup
    => Initialising new SSH agent...
    ssh-add
    # enter passphrase, NOT archer password, what you entered
    # when you ran 
    # $ source ~um/um-training/install-ssh-keys <archer-username>@login.archer.ac.uk
    ssh mmuetz@login.archer.ac.uk
    # Should log you in without having to enter password.

Extra info
----------

* The line at the end of .bashrc is to setup MOSRS access (not archer):
    * . mosrs-setup-gpg-agent
* The line at the end of .profile is to setup the ssh-agent:
    * . $HOME/.ssh/ssh-setup

References
==========

* [Recommended way to fix problem](http://cms.ncas.ac.uk/wiki/FAQ_T4_F5)
* [ps commands](http://cms.ncas.ac.uk/wiki/FAQ_T4_F17)
* [Genral FAQ](http://cms.ncas.ac.uk/wiki/FAQ)
* [How to create new keys/passphrase](http://cms.ncas.ac.uk/wiki/ArcherSshAgent)
