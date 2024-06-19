# Creation of a Base AMI using Packer

<details>
  <summary>Architecture</summary>
  <img src="./Images/one.png">
</details><br>

<details>
  <summary>Steps followed to create the project</summary>
  <br>
  <details class="nested">
  <summary>Create GitHub repository</summary>
       We will create a GitHub repository for Part One. This repository will serve as a central hub for developers to easily interact with the               project and manage their contributions. It will also provide a solid anchor for our Jenkins pipeline, ensuring smooth integration and                 continuous deployment processes. By utilizing GitHub, we promote collaboration, version control, and transparency within the team,                    enhancing overall productivity and project management.
  </details><br>
   
  <details class="nested">
  <summary>Launch an ec2</summary>
    We will create an EC2 instance on AWS and set up the project there. This way, the project setup won’t interfere with our local machines, and our      local setups won’t affect the project. By isolating the environment, we ensure a clean and consistent setup for everyone involved, making it easier to manage dependencies and configurations. Additionally, this approach allows for better scalability and flexibility as we can easily         replicate the environment or scale resources as needed.
  </details>

  <details class="nested">
  <summary>Installations</summary>
  1. Install Jenkins on this EC2: Using Jenkins as our automation tool, we connect with our Version Control System (VCS) to streamline the code 
  deployment process. Jenkins uses pipelines to automate the steps needed to build an Amazon Machine Image (AMI) on AWS. This setup makes our 
  deployment process faster, more reliable, and consistent..<br>
  2. Install the latest version of Java: Jenkins will also need Java to run.<br>
  3. Installation steps:
  <pre><code>  
    sudo apt update
sudo apt install openjdk-11-jdk
java --version
wget -p -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
sudo apt update
sudo apt install jenkins
sudo systemctl status jenkins
sudo systemctl start jenkins
 </code> </pre></details>

  <details class="nested">
  <summary>Packer configuration</summary>
  </details>

  <details class="nested">
  <summary>Provisioner</summary>
  </details>

  <details class="nested">
  <summary>Launch Jenkins and Create a Pipeline with the following stages</summary>
  </details>

  <details class="nested">
  <summary>Check for the ami on AWS Console</summary>
  </details>
  
  </details>

