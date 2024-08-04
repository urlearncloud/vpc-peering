# vpc-peering



VPC peering is a networking connection established between two VPCs that enables you to route traffic between them using private IP addresses.

VPC peering is essential for enabling private communication between VPCs without relying on public IPs or the internet. 

It facilitates secure and efficient sharing of resources across different VPCs, whether they reside within the same account, different accounts, or even different regions.


### Task 1: Creating Two VPCs

vpc-1    ------>   ip = 10.100.0.0/16


vpc-2   --------->   ip =  10.200.0.0/16


### Task 2: Creating Internet gateway


igw-1-vpc-1   &  attach to vpc-1


igw-1-vpc-2   &  attach to vpc-2


### Task 3: Creating Subnets


subnet-1-vpc-1   ----->  vpc-1    ---->   ip = 10.100.1.0/24    ----->   az  =  ap-south-1a

subnet-1-vpc-2   ----->  vpc-2    ---->   ip = 10.200.1.0/24    ----->   az  =  ap-south-1b



### Task 4: Creating Route tables


rt-1-vpc-1   ----->   vpc-1   ---->  associate  subnet-1-vpc-1  &  mention  igw-1-vpc-1

rt-1-vpc-2   ----->   vpc-2   ---->  associate  subnet-1-vpc-2  &  mention  igw-1-vpc-2



### Task 5: Creating EC2 instances


Name  =  firstinstance    ------>    AMI   =  Ubuntu-22     ------>   KEYPAIR  =  peer-key.pem   

vpc  =  vpc-1    ---->  autoassign-pub-ip  =  enable     ----->   SG  =  vpc1-sg ( alltraffic  -->  anywhere )

userdata  :-  paste userdata code-for-server1



Name  =  secondinstance    ------>    AMI   =  Ubuntu-22     ------>   KEYPAIR  =  peer-key.pem   

vpc  =  vpc-2    ---->  autoassign-pub-ip  =  enable      ----->   SG  =  vpc2-sg ( alltraffic  -->  anywhere )

userdata  :-  paste userdata code-for-server2
