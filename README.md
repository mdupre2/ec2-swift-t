# ec2-swift-t

##Description
A set of scripts to make running swift jobs on ec2 easier
* 'ec2-ip': Retreives the list of public ip addresses of all running ec2 instances and stores them in 'public_ip.txt'. Retreives the list of private ip addresses of all running ec2 instances and stores them in 'private_ip.txt'
	Usage: ec2-ip
* 'ec2-turbine' : runs turbine on the ec2 instance. Any command-line arguements used in turbine can be used with this script
	Usage:  ec2-turbine program.tic [COMMANDS] 
