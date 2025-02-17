# Introduction-to-jenkins

# Introduction To CICD
continuous Integration and Continuous Delivery (CI/CD/is a set of best practices and methodologies that revolutionize the software development lifecycle by enhancing efficiency, reliability, and speed. CI/CD represents a seamless integration of automation and collaboration throughout the development process, aiming to deliver high-quality software consistently and rapidly. In the realm of CI, developers regularly integrate their code changes into a shared repository, triggering automated builds and tests to detect integration issues early. On the other hand, CD encompasses both Continuous Delivery and Continuous Deployment, ensuring that software is always in a deployable state and automating the deployment process for swift and reliable releases, The CI/CD pipeline fosters a culture of continuous improvement, allowing development teams to iterate
quickly, reduce manual interventions and deliver sottware with confidence.

# What is Jenkins

Jenkins is widely employed as a crucial CI/CD tool for automating software development processes. Teams utilize Jenkins to automate building, testing, and deploying applications, streamlining the development lifecycle. With Jenkins pipelines, developers can define, version, and execute
entire worklows as code, ensuring consistent and reproducible builds. Integration with version control systems allows Jenkins to trigger builds automatically upon code chandes, faciltating early detection of issues and enabling teams to deliver high-quality software at a faster pace.
Jenkins' fexibility extensibility through plugins, and supportt for various tools make it a preffered choice for organizations ain=ming to implement efficient and automated DevOps practice.


# Project goals
By the end on this project you should have:

* Developed a foundational understanding of Continuous Integration (Cl) and Continuous Delivery (CD) principles, and articulate their role in improvina software development processes
* Acquired proficiency in using Jenkins by mastering installation, configuration, and navigation through the Jenkins user interface, and gain hands-on experience in creating and managing Jenkins jobs
* Learned the end-to-end process of automating software builds, running automated tests, and deploying applications using Jenkins, fostering a practical understanding of CI/CD pipelines.
* Apply best practices in CI/CD processes, including parameterized builds, integration with externa
tools, and leveraging containerization technologies like Docker

# Project Highlight

* Introduction To CICD
* What is Jenkins
* Project Pre-requisites
* Project Gaols
* Getting Started With Jenkins
* Jenkins Job
* Creating g Freestyle Project
* Connecting Jenkins To Our Source Code Management
* Configuring Build Trigger
* Creating a Pipeline Job
* Configuring Build Trigger
* Writing Jenkins Pipeline Script
* Installing Docker
* Building Pipeline Script

# Getting Started With Jenkins

Now that we have an idea what jenkins, let's dive in to installing jenkins

*Update package repositories*

```
sudo apt update

```

*Install JDK*

```
sudo apt install default-jdk-headless

```

*Install Jenkins*

```
    wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
    sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > \
    /etc/apt/sources.list.d/jenkins.list'
    sudo apt update
    sudo apt-get install jenkins
```

**The command installs Jenkins. It involves importing the Jenkins GPG key for package venfication, adding the Jenkins repository to the systems sources, updating package lists, and finally, installing Jenkins through the package manager (apt-get).**

*Check if Jenkins has been install and is up and running*

```
sudo systemctl status jenkins

```
![image](https://github.com/user-attachments/assets/0b0b37fc-a38d-4779-b158-671cfdbafd21)


**On our Jenkins instance, create new inbound rules for port 8080 in security group**

By default, jenkins listens on port 8080, we need create an inbound rule for this in the security group of our jenkins instance

![image](https://github.com/user-attachments/assets/15b44b63-d74c-44ae-8f33-19a82d8cf863)


**Set up Jenkins Web Console**

i. Input your Jenkins Instance ip address on your web browser i.e. http://public_ip_address:8080
ii. On your Jenkins instance, check "/var/lib/jenkins/secrets/initialAdminPassword to know your password.

![image](https://github.com/user-attachments/assets/37bcacb4-4286-4443-af98-94bac8ed52e7)

![image](https://github.com/user-attachments/assets/c3ddb370-896b-466b-8eda-0c486d7d05f8)

iii. Install suggested plugins

![image](https://github.com/user-attachments/assets/13880a02-ccd5-4620-8832-ccb191aac475)

iv. Create a user account

![image](https://github.com/user-attachments/assets/3c13be54-7f34-4b71-a950-341b03c158da)

v. Login to the Jenkins console

![image](https://github.com/user-attachments/assets/6911e2b7-c4d1-439b-8ac5-d95c21277227)


# Jenkins free style 

Jenkins Job
In Jenkins, a job is a unit of work or a task that can be executed by the Jenkins automation server.
A Jenkins job represents a specific task or set of tasks that needs to be performed as part of a build or deployment process. Jobs in Jenkins are created to automate the execution of various steps such as compiling code, running tests, packaging applications, and deploying them to servers. Each Jenkins job is configured with a series of build steps, post-build actions, and other settings that define how the job should be executed.

# Creating a Freestyle Project
Let's create our first build job
i. From the dashboard menu on the left side, click on new item

![image](https://github.com/user-attachments/assets/21cb7518-59b3-4e2d-86f2-1e85f78d6cd2)

ii. Create a freestyle project and name it "my-first-job"

![image](https://github.com/user-attachments/assets/43751108-683f-4602-8861-d3510eac6352)

# Connecting Jenkins To Our Source Code Management

Now that we have created a freestyle project, let connect jenkins with github.

i.  Create a new repository called jenkins-scm with a README.md file

ii. Connect "jenkins' to 'jenkins-scm' repository by pasting the repository url in the area selected below. Make sure your current branch is 'main'


<img width="1173" alt="image" src="https://github.com/user-attachments/assets/42e051db-960e-4980-a26d-52642f028d96" />


<img width="1220" alt="image" src="https://github.com/user-attachments/assets/491afcf0-cc18-4da4-beed-9f754e3cdd60" />


iii. Save configuration and run "build now" to connect jenkins to our repository

<img width="1031" alt="image" src="https://github.com/user-attachments/assets/30b88a44-236c-4b9a-b1ef-6560bdad2549" />

We have successfully connected jenkins with our github repository (jenkins-scm)

Configuring Build Trigger

As a engineer, we need to be able to automate things and make our work easier in possible ways. We have connected "jenkins' to 'jenkins-scm', but we cannot run a new build with clicking on

'Build Now'. To eliminate this, we need to conflure a build trigger to our jenkins job. With this, jenkins will run a new build anytime a change is made to our github repository

i. Click "Configure" your job and add this configurations

ii. Click on build trigger to configure triggering the job from GitHub webhook

![image](https://github.com/user-attachments/assets/9fbd2376-4a42-4c0d-bf58-9804229802e9)

iii. Create a github webhook using jenkins ip address and port

<img width="945" alt="image" src="https://github.com/user-attachments/assets/633eb70e-54fb-47cc-8c47-d1c39609380a" />

![image](https://github.com/user-attachments/assets/6bb3d016-1093-4565-a3b0-91ebbd428ccb)



















