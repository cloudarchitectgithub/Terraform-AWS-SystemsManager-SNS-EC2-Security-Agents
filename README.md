# Implementation of a Set of EC2 Instances using Terraform and AWS Systems Manager Configuration with Amazon Simple Notification Service for Automated Installation of Security Officers

<p align="center">
  <img src="https://i.imgur.com/KD0wIVl.png" height="80%" width="80%" alt="Terraform and AWS Systems Manager Banner"/>
</p>

## Project Description
This project focuses on automating infrastructure deployment and instance management using Terraform and AWS Systems Manager. The first part of the project involves setting up AWS infrastructure using Terraform, a popular infrastructure-as-code (IaC) tool, to create and provision resources on AWS. The second part of the project focuses on managing the deployed instances using AWS Systems Manager, which allows for remote instance management, configuration, and monitoring. This approach aims to simplify infrastructure management, improve operational efficiency, and reduce manual effort for configuring and maintaining cloud resources.

## Project Objectives
1. **Automate AWS Infrastructure Deployment:** Use Terraform to ensure consistent, repeatable, and efficient creation of cloud resources.
2. **Leverage AWS Systems Manager:** Manage instances remotely, handle configurations, and monitor performance.
3. **Implement Best Practices for Infrastructure as Code (IaC):** Ensure scalability, version control, and easy collaboration.
4. **Reduce Operational Overhead:** Automate routine management tasks, such as configuration updates and software patching.
5. **Enable Cost-Effective Infrastructure Management:** Minimize manual intervention and ensure quick responses to issues through automation.

---

## Tools and Technologies
- **Visual Studio Code (VS Code):** A code editor used for writing and editing Terraform scripts and configuration files.
- **Terraform:** An infrastructure-as-code tool for provisioning AWS resources.
- **AWS Systems Manager:** A service for managing and automating tasks on EC2 instances.
- **AWS EC2:** Virtual servers used for hosting applications.
- **AWS IAM:** Identity and Access Management for managing permissions.
- **AWS CloudFormation:** For template-based resource management (if applicable).

---

## Project Solution

### Part 1: Terraform Setup for Infrastructure Provisioning
1. **Download and Install Visual Studio Code:** The first step was downloading VS Code to edit Terraform configuration files.
2. **Launch Cloud9 IDE:** Cloud9 was used to set up the development environment, allowing easy integration with AWS resources.
3. **Create Terraform Configuration:** Terraform scripts were created to provision AWS resources like EC2 instances, VPCs, subnets, and security groups. The infrastructure was defined in Terraform as code, ensuring that all resources were properly configured.
4. **Run Terraform to Deploy Infrastructure:** Terraform was executed to apply the configurations, automatically setting up the defined resources in AWS. The infrastructure was fully automated and provisioned using a few commands.

### Part 2: AWS Systems Manager Setup for EC2 Management
1. **Search for AWS Systems Manager:** From the AWS Management Console, AWS Systems Manager was accessed to initiate instance management.
2. **Quick Setup for Systems Manager:** The user navigated to the left-hand menu, clicked on Quick Setup, and configured the Host Management option to manage the EC2 instances created via Terraform.
   - Upon first accessing Systems Manager, the user confirmed the region (Northern Virginia, us-east-1).
3. **Create a New Configuration:** In the Quick Setup, the configuration was defined as Host Management and proceeded to the next step.
4. **Select EC2 Instances:** The targets for the configuration were the EC2 instances created earlier. The option to manually select instances from the current region was chosen.
5. **Install Systems Manager Agent:** The Systems Manager agent was installed on all selected EC2 instances, enabling the control and management capabilities provided by Systems Manager.
6. **Monitor Configuration Status:** The configuration process initiated and monitored through Systems Manager, with deployment statuses displayed to ensure success. Once the association status became green, the instances were ready for further Systems Manager operations.
7. **Use Systems Manager Run Command:** Systems Manager was configured to remotely execute tasks on the EC2 instances, including security patching and software updates.

---

## Step-by-Step Directions

### Step 1: Download and Install Visual Studio Code
1. **Download Visual Studio Code:** Visit [https://code.visualstudio.com/](https://code.visualstudio.com/) and download the installer for your operating system.

<p align="center">
  <img src="https://i.imgur.com/D7JztlF.png" height="80%" width="80%" alt="VS Code Download Screenshot"/>
</p>

2. **Install VS Code:** Run the installer and follow the prompts to install Visual Studio Code on your machine.

---

### Step 2: Set Up Your AWS Account
1. **Create an AWS Account:** If you don't have an AWS account, sign up at [aws.amazon.com](https://aws.amazon.com/).

<p align="center">
  <img src="https://i.imgur.com/98PpTuN.png" height="80%" width="80%" alt="AWS Signup Screenshot"/>
</p>

2. **Configure AWS CLI:** Install the AWS Command Line Interface (CLI) and configure it using the command `aws configure`. Enter your AWS access key, secret key, region, and output format.

---

### Step 3: Install Terraform
1. **Download Terraform:** Go to the Marketplace on VS Code and download Terraform.

<p align="center">
  <img src="https://i.imgur.com/NHfAyX6.png" height="80%" width="80%" alt="Terraform Download Screenshot"/>
</p>

2. **Install Terraform:** Click the “Install” tab.

---

### Step 4: Create Your Terraform Configuration
1. **Open VS Code:** Launch Visual Studio Code.
2. **Create a New Project Folder:** Create a new folder for your Terraform project.
3. **Create Terraform Files:** Within the project folder, create a file named `main.tf` to define your infrastructure.
4. **Define Providers and Resources:** Write the Terraform code to define the AWS provider and the EC2 instances you want to provision. Example configuration:

<p align="center">
  <img src="https://i.imgur.com/fWao4NS.png" height="80%" width="80%" alt="Terraform Configuration Screenshot"/>
</p>

<p align="center">
  <img src="https://i.imgur.com/X2TNtdA.png" height="80%" width="80%" alt="Terraform Configuration Screenshot"/>
</p>

5. **Zip File:** Zip the Terraform folder you created with `main.tf` and `provider.tf`.

6. **Create Key Pairs to Connect to EC2 Instance:** Under “Networking & Security,” click “Key Pairs,” then click “Create Key Pair.” Name the key `sshkey1`.

<p align="center">
  <img src="https://i.imgur.com/svr2LbP.png" height="80%" width="80%" alt="Key Pair Creation Screenshot"/>
</p>

---

### Step 5: Initialize Terraform
1. **Open AWS CloudShell CLI:** Use the terminal in AWS CloudShell to install Terraform.

<p align="center">
  <img src="https://i.imgur.com/eYLOyRc.png" height="80%" width="80%" alt="AWS CloudShell Screenshot"/>
</p>

2. **Initialize the Terraform Configuration:** Run the command `terraform init` to initialize the working directory containing Terraform configuration files.
   - Install Terraform on AWS Cloud Shell:
     ```bash
     sudo yum install -y yum-utils
     sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/AmazonLinux/hashicorp.repo
     sudo yum -y install terraform
     terraform -v
     ```

<p align="center">
  <img src="https://i.imgur.com/fO02lrQ.png" height="80%" width="80%" alt="Terraform Installation Screenshot"/>
</p>

3. **Upload Terraform Zip File to CloudShell:**

<p align="center">
  <img src="https://i.imgur.com/7aH2IaS.png" height="80%" width="80%" alt="Terraform Upload Screenshot"/>
</p>

---

### Step 6: Plan Your Infrastructure
1. **Create an Execution Plan:** Run `terraform init` to download the Terraform provider locally.

<p align="center">
  <img src="https://i.imgur.com/D1BFcBV.png" height="80%" width="80%" alt="Terraform Init Screenshot"/>
</p>

2. **Run `terraform plan`:** Create an execution plan and review the resources that Terraform will create.

<p align="center">
  <img src="https://i.imgur.com/1AAEXBP.png" height="80%" width="80%" alt="Terraform Plan Screenshot"/>
</p>

---

### Step 7: Apply Your Configuration
1. **Provision the Resources:** Run `terraform apply` and confirm to apply the changes and provision the defined resources in AWS.

<p align="center">
  <img src="https://i.imgur.com/h5aIQjM.png" height="80%" width="80%" alt="Terraform Apply Screenshot"/>
</p>

---

### Step 8: Set Systems Manager Notifications via Amazon SNS
1. **Configure IAM Roles:** Ensure that the EC2 instances have the appropriate IAM roles to use AWS Systems Manager. Create a role with the `AmazonEC2RoleforSSM` policy and attach it to your instances.

<p align="center">
  <img src="https://i.imgur.com/GZtGx6Z.png" height="80%" width="80%" alt="IAM Role Configuration Screenshot"/>
</p>

2. **Create an SNS Topic:**
   - Go to the Amazon SNS console.
   - Click **Create Topic**.
   - Choose the topic type as **Standard** and give it a name like `SystemsManagerToSNS`.
   - Click **Create topic**.

<p align="center">
  <img src="https://i.imgur.com/4YSQoJj.png" height="80%" width="80%" alt="SNS Topic Creation Screenshot"/>
</p>

3. **Subscribe to the SNS Topic:**
   - In the SNS console, click the **Subscriptions** tab.
   - Click **Create subscription**.
   - In the **Protocol** dropdown, choose **Email** (or whichever method you prefer for receiving notifications).
   - Enter your email address or phone number (depending on the protocol chosen) in the endpoint field.
   - Click **Create subscription**. You’ll need to confirm your subscription by checking your email (or SMS) and clicking on the confirmation link.

<p align="center">
  <img src="https://i.imgur.com/F3aPU9D.png" height="80%" width="80%" alt="SNS Subscription Screenshot"/>
</p>

<p align="center">
  <img src="https://i.imgur.com/D3zGXlS.png" height="80%" width="80%" alt="SNS Subscription Confirmation Screenshot"/>
</p>

<p align="center">
  <img src="https://i.imgur.com/DhAaXCT.png" height="80%" width="80%" alt="SNS Subscription Confirmation Email Screenshot"/>
</p>

---

### Step 9: Detailed Steps for AWS Systems Manager Setup
1. **Access AWS Systems Manager:**
   - In the search bar at the top, type "Systems Manager" and click on it from the drop-down results.

<p align="center">
  <img src="https://i.imgur.com/mn7tdYZ.png" height="80%" width="80%" alt="AWS Systems Manager Access Screenshot"/>
</p>

2. **Confirm Region Selection:**
   - When you first access Systems Manager, it may ask you to confirm the region in which you want to operate.
   - Select the region you’re using for your resources, e.g., US East (N. Virginia) (us-east-1), and confirm.

<p align="center">
  <img src="https://i.imgur.com/mGY4b0m.png" height="80%" width="80%" alt="AWS Region Selection Screenshot"/>
</p>

3. **Navigate to Quick Setup:**
   - On the left-hand side of the Systems Manager dashboard, look for the menu.
   - Scroll down and click on **Quick Setup**.

<p align="center">
  <img src="https://i.imgur.com/WVXRF3j.png" height="80%" width="80%" alt="Quick Setup Screenshot"/>
</p>

4. **Create a New Configuration:**
   - On the Quick Setup screen, click on the button labeled **Create** to start a new configuration.
   - Under the **Configuration Type** section, select **Host Management** from the options presented.

<p align="center">
  <img src="https://i.imgur.com/2AZv2xq.png" height="80%" width="80%" alt="Host Management Configuration Screenshot"/>
</p>

5. **Select EC2 Instances (Targets):**
   - In the **Targets** section, choose **Manual Selection**. This will allow you to manually select the EC2 instances you want to configure.
   - Select the EC2 instances that were created through your Terraform configuration.
   - After selecting the instances, click **Create** to apply the configuration.

<p align="center">
  <img src="https://i.imgur.com/LI4avTc.png" height="80%" width="80%" alt="EC2 Instance Selection Screenshot"/>
</p>

<p align="center">
  <img src="https://i.imgur.com/td83xFS.png" height="80%" width="80%" alt="EC2 Instance Selection Screenshot"/>
</p>

6. **Wait for Configuration Deployment:**
   - Once you hit **Create**, Systems Manager will initiate the configuration process on your selected EC2 instances.
   - Monitor the progress of the configuration under the **Configuration Deployment Status** section.
   - Once the process is complete, the **Association Status** will show as **Success** and turn green.

<p align="center">
  <img src="https://i.imgur.com/h16ACXq.png" height="80%" width="80%" alt="Configuration Deployment Status Screenshot"/>
</p>

7. **Use Run Command to Install the Security Agent:**
   - In the Systems Manager menu, navigate to **Run Command**.
   - Click on **Run a Command** to initiate the process.
   - From the list of available documents, select **AWS-RunShellScript**.
   - In the **Commands** section, enter the shell script that will install the simulated security agent on your EC2 instances.

<p align="center">
  <img src="https://i.imgur.com/CHXoP6Q.png" height="80%" width="80%" alt="Run Command Screenshot"/>
</p>

<p align="center">
  <img src="https://i.imgur.com/TT7u4cX.png" height="80%" width="80%" alt="Run Command Screenshot"/>
</p>

8. **Set Up SNS Notifications:**
   - To receive notifications about the status of your Run Command executions, configure an SNS (Simple Notification Service) topic.
   - In the AWS Management Console, search for **SNS** and click on it.
   - Create a new SNS topic by clicking **Create Topic**, and provide a name, e.g., `RunCommandNotifications`.
   - Set up your email or another notification channel as the **Subscription** for this topic.
   - In Systems Manager, return to the **Run Command** screen and, during the next command execution, set this SNS topic under the **Notifications** section.

<p align="center">
  <img src="https://i.imgur.com/JJrzhgr.png" height="80%" width="80%" alt="SNS Topic Setup Screenshot"/>
</p>

<p align="center">
  <img src="https://i.imgur.com/wHRR757.png" height="80%" width="80%" alt="SNS Subscription Setup Screenshot"/>
</p>

<p align="center">
  <img src="https://i.imgur.com/xBIR42i.png" height="80%" width="80%" alt="SNS Notification Setup Screenshot"/>
</p>

9. **Monitor the Run Command Execution:**
   - After running the command, Systems Manager will display the status of the execution.
   - View the output logs for each EC2 instance to verify whether the security agent was installed successfully.

<p align="center">
  <img src="https://i.imgur.com/qlrUidp.png" height="80%" width="80%" alt="Run Command Execution Screenshot"/>
</p>

<p align="center">
  <img src="https://i.imgur.com/1HcBXb0.png" height="80%" width="80%" alt="Run Command Execution Screenshot"/>
</p>

10. **Clean Up Resources Using Terraform:**
    - Once the project is completed, clean up the infrastructure you created using Terraform.
    - Open a terminal and navigate to the directory containing your Terraform configuration files.

---

## Project Conclusion
The project successfully implemented an automated infrastructure provisioning and management solution using Terraform and AWS Systems Manager. Terraform enabled the automated creation of scalable and repeatable infrastructure, while AWS Systems Manager provided an efficient way to manage and monitor EC2 instances. The integration of these two services streamlined the deployment process, significantly reducing manual intervention and improving operational efficiency.

---

## Challenges Encountered
1. **Terraform Configuration Issues:** Initial difficulties were encountered while configuring Terraform scripts, particularly in aligning security group settings with VPC configurations. These were resolved through careful review and trial-and-error testing.
2. **AWS Systems Manager Agent Installation:** A delay was experienced in getting the Systems Manager agent installed on all EC2 instances. This was due to network connectivity issues, which were resolved by adjusting the security group settings to allow the necessary traffic.
3. **Cross-Region Resource Management:** Ensuring that all resources were properly managed within a single AWS region required careful attention to region-specific settings in both Terraform and AWS Systems Manager.

---

## Lessons Learned
1. **Infrastructure as Code (IaC) Provides Significant Time Savings:** Using Terraform to define infrastructure as code allowed for rapid deployment and easy repetition of the environment, proving highly efficient.
2. **AWS Systems Manager Simplifies Instance Management:** The ability to manage multiple EC2 instances through a centralized service like AWS Systems Manager greatly reduces operational overhead, especially in managing security and updates.
3. **Monitoring is Critical:** The integration with AWS CloudWatch and Systems Manager highlights the importance of monitoring infrastructure for early detection of issues.
