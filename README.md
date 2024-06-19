# Creation of a Base AMI using Packer

<details>
  <summary>Architecture</summary>
  <img src="./Images/one.png">
</details>

<details>
  <summary>Steps followed</summary>
    <details><summary>Create Gitlab repository</summary>
    1. Create Gitlab Group & Project
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c47b3329-2888-4c1f-b29a-8554e42006ec/Untitled.png)
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0dee62a4-bd9c-42c5-8285-2db2f7b267e6/Untitled.png)
    
    1. Create Environment based branching strategy
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3a8741d9-bd36-42dc-baf0-9304060c2516/Untitled.png)
    
    1. Assign roles
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c199dcd4-0ffa-4601-9e9f-b95ded2c51e0/Untitled.png)
    
    1. Protect the branches.
        
        ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/cbdf7188-37bf-4fd8-980b-48d1cfb47768/Untitled.png)
  </details>      
- Launch an EC2
    - We can launch this EC2 manually from AWS Console or via Terraform 
    (I chose Terraform)
    - So I will be generating terraform code in my laptop and provision an EC2 on AWS
- Installations
    - Install Jenkins on this EC2 because:
        
        Because we are using Jenkins as an automation tool. It will pick the code from VCS and with help of pipelines, it will build the AMI on AWS
        
        - What else Jenkins need?
            
            It needs Java to run Jenkins.
            
        - Installation steps:
            - sudo apt update
            - sudo apt install openjdk-11-jdk
            - java --version
            - wget -p -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
            - sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
            - sudo apt update
            - sudo apt install jenkins
            - sudo systemctl status jenkins
            - sudo systemctl start jenkins
    - Install Packer on this EC2 (only from the installation steps below), because:
        - Because we are using Hashicorp Packer to *automate* building AMI with Jenkins Pipeline.
        - So wherever Jenkins is installed, in the same machine Packer should be available
        - Installation steps:
            - install wget of you dont have
            - wget https://releases.hashicorp.com/packer/1.9.1/packer_1.9.1_linux_amd64.zip
            - unzip packer_1.9.1_linux_amd64.zip
            - packer always goes to environmnet path variable /usr/local/sbin/packer
                - From this location you need to execute ./packer
                - But from other locations commands will not work
            - Thats why we need to set environment variable
                - go to location where packer is downloaded
                - cp packer /usr/local/sbin/
    - Install Git
        
        In order to clone the git repository
        
    - Install awscli and configure AWS
        
        ```yaml
        sudo apt install awscli -y
        ```
        
        Run:    aws configure
        
        Provide AWS Access key and Secret Key and select the region which you want to build your ami.
        
- Packer configuration
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/dbc266d4-05a5-4014-b6c4-ce5bee2c0432/Untitled.png)
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2da88c85-f23b-4195-9e6f-a2d9c23786ce/Untitled.png)
    
- Provisioner.sh
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/898cb815-ab6c-4209-9290-7b37a3384e69/Untitled.png)
    
- Launch Jenkins and Create a Pipeline with following stages
    
    We are going to write the pipeline in Jenkinsfile. And the Jenkinsfile contains:
    
    1. Git checkout
        - It picks the code from VCS where our Packer code and Playbook is present.
        
        ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0f6c8f47-64cd-4154-89e3-1e4adae546f3/Untitled.png)
        
    2. Build AMI
        - It will run Packer commands integrating with Shell Module to build AMI.
        
        ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e9eb6d24-8d10-4956-90e6-dd4a41d48ea2/Untitled.png)
        
        ![24.07.2023_21.59.55_REC.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8411188b-584b-4dd5-8a24-51c57cfd5949/24.07.2023_21.59.55_REC.png)
        
- See the ami on AWS Console
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e0bee9bb-c1f5-4937-a19c-16e88c945ceb/Untitled.png)
</details>

