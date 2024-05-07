# MongoDB basic commands and notes

+ Replica Sets
  + When different mongod or mongod instances have the same databases
  + This is to ensure redundancy of the DBs
  + It is usually a primary mongod instance with write and read permissions on the instance set
  + Then there is secondary instances that have read only permissions and copy whatever the primary has on its records
  + So every mongod instance has different roles for them.
  + If a primary node dies the replica set configuration creates an election to vote who of the secondary instances will become the new primary
  + The replica sets needs at least three instances on the set
  + Uneven number of voting replica set membes is recommended

+ How to create replicaset
  + Keyfile
    + This keyfile enables us authentication via well key fial
    + This is the minimun of security so that the replicas can authenticate
    + For production it is better to use X.509
    + We have to give user permissions for the file
      + chmod 400 keyfile (insert reference to linux notes)
  + Then we need to create a directory for each mongod process so that they can store their individual data

## Commands

+ **mongod**
  + it is like the basic command for mongodb that calls the systemd service on systemctl
  + Default Settings
    + Port: 27017
    + Storage: /data/db
  + mongod --dbpath {path_in_filesystem}

+ mongosh
  + It initiates the mongoshell

+ show databases
  + It shows all databases on system

+ db.{dbName}.insertOne({document_to_insert})
  + Inserts an entry of whatever databases there is
