# ec2-swift-t

##Description
A set of scripts to make running swift jobs on ec2 easier

* `ec2-ip`: Retreives the list of public ip addresses of all running ec2 instances and stores them in `public_ip.txt`. Retreives the list of private ip addresses of all running ec2 instances and stores them in `private_ip.txt`
```
     Usage: ec2-ip
```
* `ec2-turbine` : runs turbine on the ec2 instance. Any command-line arguements used in turbine can be used with this script
```
     Usage: ec2-turbine program.tic [COMMANDS] 
```
* `ec2-push` : push a file on local machine to all ec2 instances
```
     Usage: ec2-push  local_sorce_file insance_target_file
```
* `ec2-pull` : pulls files from all ec2 instances and stores in local directory
```
     Usage: ec2-pull  insance_source_file local_target_directory
``` 
* `ec2-push-head` : push a file on local machine to head ec2 instance
```
     Usage: ec2-push-head  local_sorce_file insance_target_file
```
* `ec2-pull-head` : pulls file from head ec2 instances and stores in locally
```
     Usage: ec2-pull-head  insance_source_file local_target_file
``` 
* `ec2-mkdir` : makes directory on all ec2 instances
```
     Usage: ec2-mkdir insance_new_directory
``` 
* `ec2-mkdir-head` : makes directory on head ec2 instance
```
     Usage: ec2-mkdir-head  insance_new_directory
```
* `ec2-rm` : remove file on all ec2 instances
```
     Usage: ec2-rm insance_file
``` 
* `ec2-rm-head` : removes file on head ec2 instance
```
     Usage: ec2-rm-head  insance_file
```

##Setup
1. Create ec2 instances. Note that micro instances do not have enough ram to run Swift/T. All insances must have Swift installed. Having all the instances look the same is helpful. 
2. Fill in `ec2-config` file. Note that any environment variables exported in ~/.bashrc of the instance will not be exported. export all environment variables in ~/.profile. If turbine's binary location is added to $PATH in .bashrc, the full path of the turbine binary will need to be stored in  `SWIFT_EC2_TURBINE_PATH` in `ec2-config`
3. If you don't have a AWS user with administative permissions [create a user](http://docs.aws.amazon.com/IAM/latest/UserGuide/ManagingCredentials.html). 
4. Use the downloaded credentials to fill in `AWS_ACCESS_KEY` and `WS_SECRET_KEY` in `ec2-config`
5. One of the instances must be designated the head node. The head node has a private key in its ~/.ssh folder and the rest have the matching public key(.pem) in it's  ~/.ssh folder. The keys can be made with ssh-keygen and pushed to the nodes with `ec2-push` and `ec2-push-head`.
6. All instance must have a folder called `swift-run` in the home directory. This is where swift will be ran on each of the instances. You can use `ec2-mkdir` to create this directory. 

##Usage
1. Whenever new instances are started `ec2-ip` must first be called
2. Change the first line of `head_node_public_ip.txt` to the public ip of the head node
3. Now you can use any of the scripts.


