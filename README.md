# Creation of a Base AMI using Packer

<details>
  <summary>Architecture</summary>
  <img src="./Images/one.png">
</details>

<details>
  <summary>Steps followed to create the project</summary>
  <br>
  <details class="nested">
  <summary>Create GitHub repository</summary>
  Create a GitHub repo for Part One as it will be helpful for developers to interact easily and have an anchor for the Jenkins pipeline.
  </details>

  <details class="nested">
  <summary>Launch an ec2</summary>
    We will be creating an ec2 instance in AWS and following everything inside it so that the project setup does not interfere with any of our local machine setups and vice versa.
  </details>

  <details class="nested">
  <summary>Installations</summary>
  1. Install Jenkins on this EC2: Because we are using Jenkins as an automation tool. It will pick the code from VCS and with help of pipelines, it     will build the AMI on AWS.
  2. Install the latest version of Java: Jenkins will also need Java to run.
  3. Installation steps:
  </details>

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

