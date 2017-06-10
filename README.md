
This script is pumping!

--- 

You can use it with the following command to start all machines
$ vagrant up

If you want to start only one machine, you can do something like
$ vagrant up master
$ vagrant up slave1


After provisioning all machines, you must run these two commands as hduser@master.
$ hadoop namenode -format
$ $HADOOP_HOME/sbin/start-dfs.sh

---

I used this blog as reference to implement it.
http://www.michael-noll.com/tutorials/running-hadoop-on-ubuntu-linux-multi-node-cluster/

--- 

TODOS 

Next step: generalize it to provision n machines. It is simple, and with some minutes
of ruby programming, I'll be able to do it.

--- 

Thank you

github.com/zembrzuski
https://www.linkedin.com/in/rodrigo-claro-zembrzuski/

