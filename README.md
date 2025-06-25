<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Set Up a Web App in the Cloud

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-devops-vscode)

**Author:** Vijay Pratap Singh Hada  
**Email:** vijaypratapsinghhada9@gmail.com

---

## Set Up a Web App Using AWS and VS Code

![Image](http://learn.nextwork.org/blissful_yellow_calm_donkey/uploads/aws-devops-vscode_7a1de541)

---

## Introducing Today's Project!

Today, I'll create a new cloud server using AWS EC2, connect to it from my laptop using VS Code, and set up a simple web app with Java and Maven. This will teach me how to launch and connect to servers in the cloud, use key pairs for secure login, and build a basic app from scratch—all important DevOps skills for automating software delivery.

### Key tools and concepts

Services I used were AWS EC2 and VS Code. Key concepts I learned include launching and connecting to cloud instances, setting up secure key pairs, using SSH for remote access, and employing Maven and Java for web application development.

### Project reflection

I was surprised by how straightforward it was to connect VS Code directly to the EC2 instance for seamless code editing, which greatly streamlined the development process.

This project took me approximately 3 hours and 30 minutes to complete.



This project is part one of a series of DevOps projects where I'm building a CI/CD pipeline! I'll be working on the next project whenever new information or instructions are provided. As an AI, I'm always ready to assist and process the next steps of your DevOps journey as soon as you present them.

---

## Launching an EC2 instance

I started this project by launching an EC2 instance because i need virtual computer for project and using virutal computer i can set CPU, memory, storage, and networking for specific need  for use case.


### I also enabled SSH

SSH is a secure network protocol that allows authorized users to access a remote server. It encrypts all communication between your computer and the server, ensuring that data transferred, like commands and responses, remains private. I enabled SSH so that my EC2 instance can be securely accessed and managed using my private key, ensuring only I can connect and interact with it.

### Key pairs

A key pair is a digital credential, like a secure key for a virtual computer, enabling safe access to an EC2 instance. It comprises a public key stored by AWS and a private key downloaded by the user. I'll use the RSA algorithm for cryptographic keys, a widely trusted and secure choice. The private key will be in the .pem format, which stands for Privacy Enhanced Mail. This format is a standard for cryptographic keys because it is compatible with various server types, ensuring secure and verified access to the virtual machine.

Once I set up my key pair, AWS automatically downloaded the private key to my local computer. This key is crucial for securely connecting to my EC2 instance later on.

---

## Set up VS Code

VS Code is a widely used Integrated Development Environment (IDE) that helps with creating and managing coding projects. It's like a specialized word processor for code, offering features to write, edit, and debug. Beyond basic coding, VS Code also provides tools to connect with virtual servers such as EC2 instances, making it an essential tool for remote development and cloud-based projects.

I installed VS Code primarily to establish a secure and convenient connection with my EC2 instance. This will allow me to create, modify, and manage the web application's code directly on the remote server. Essentially, VS Code will serve as my development environment, enabling seamless interaction with the cloud instance for building and deploying the application.

![Image](http://learn.nextwork.org/blissful_yellow_calm_donkey/uploads/aws-devops-vscode_53d05e68)

---

## My first terminal commands

A terminal is where you send text commands to your computer. The first command I ran for this project is c V:\Nextwork\DevOps, which allowed me to navigate into the DevOps folder where my private key file is located. This step is essential to prepare for connecting to my EC2 instance.

I also updated my private key's permissions by using `icacls` on Windows. This command helps to manage who can access files. I specifically used it to remove default permissions and then grant only read access to my user, ensuring that my private key file is secure and only I can use it.

![Image](http://learn.nextwork.org/blissful_yellow_calm_donkey/uploads/aws-devops-vscode_9328ada1)

---

## SSH connection to EC2 instance

To connect to my EC2 instance, I ran the command ssh -i nextwork-keypair.pem ec2-user@ec2-65-0-110-40.ap-south-1.compute.amazonaws.com. This command uses Secure Shell (SSH) to create a secure connection. The -i flag specifies my private key file (nextwork-keypair.pem), which authenticates my access, and ec2-user@ followed by the Public IPv4 DNS directs the connection to my specific EC2 instance.

### This command required an IPv4 address

A server's IPv4 DNS (Domain Name System) is essentially its public address on the internet. It's like a unique phone number or street address that the internet uses to locate and connect to your EC2 server. This allows your local computer to find and establish a connection with the EC2 instance, enabling communication and access to the resources hosted on that server.

![Image](http://learn.nextwork.org/blissful_yellow_calm_donkey/uploads/aws-devops-vscode_e3069dca)

---

## Maven & Java

Apache Maven is a powerful tool designed to streamline the building and management of Java software projects. It functions as a project management tool, simplifying the build process, and also acts as a package manager, automatically downloading necessary external code dependencies. Maven is particularly useful for quickly setting up web projects using "archetypes," which are templates that lay the foundation for different project types, allowing developers to focus more on coding.

Maven is required in this project because it helps build and organize Java applications. It also automates downloading necessary code, and its templates (archetypes) kickstart web projects, making setup faster so I can focus on developing the web app.

Java is a widely used programming language for developing diverse applications, from mobile apps to large enterprise systems. It's crucial for this project because Maven, which is essential for building our web app, relies on Java to function. We're specifically using Amazon Corretto 8, a free and reliable version provided by Amazon.

Java is required in this project because it is a fundamental programming language necessary for Apache Maven to operate. Since Maven will be used to generate and build our web application, having Java installed ensures that Maven can function correctly and facilitate the development process.

---

## Create the Application

I generated a Java web app using the command mvn archetype:generate -DgroupId=com.nextwork.app -DartifactId=nextwork-web-project -DarchetypeArtifactId=maven-archetype-webapp -DinteractiveMode=false. This command instructs Maven to create a new project from a web application template, setting up the basic structure and necessary files automatically, so I don't have to build it from scratch.

I installed Remote - SSH, which is a VS Code extension that enables direct, secure connections to remote servers via SSH. I installed it to allow VS Code to work on files and run programs on my EC2 instance as if they were on my local machine. This integration will significantly improve my ability to edit and manage the web app.



Configuration details required to set up a remote connection include the Host, which should match my EC2 instance's IPv4 DNS, the IdentityFile, pointing to the location of my nextwork-keypair.pem file on my local computer, and the User, which should be ec2-user. These details ensure VS Code can correctly authenticate and connect to the remote EC2 instance.

![Image](http://learn.nextwork.org/blissful_yellow_calm_donkey/uploads/aws-devops-vscode_2939cf01)

---

## Create the Application

Using VS Code's file explorer, I could see the nextwork-web-project folder, which contains all the files and subfolders that make up my web app. Specifically, I observed the src folder, holding the source code, further divided into webapp for web-related files like HTML, CSS, and JSP, and resources for configuration files. I also saw the pom.xml file, which Maven uses for project configuration. This visual access allows me to navigate and understand the project's structure directly from my local machine.

Two of the project folders created by Maven are src and webapp. The src folder holds all the source code that defines the web app's appearance and functionality. Within src, the webapp folder specifically contains the web application's files, such as HTML, CSS, JavaScript, and JSP, which are directly related to the user interface and presentation.

![Image](http://learn.nextwork.org/blissful_yellow_calm_donkey/uploads/aws-devops-vscode_45f91fd7)

---

## Using Remote - SSH

index.jsp is a file type used in Java web applications that is similar to an HTML file in that it contains markup for displaying web pages. However, index.jsp has the added capability of embedding Java code, allowing it to generate dynamic content that can change based on user input or data, unlike static HTML files.

I edited index.jsp by opening the file directly within VS Code's editor view. I then modified the placeholder code to include a personalized greeting and a message confirming the web application's functionality. After making the changes, I saved the file by pressing Command/Ctrl + S.



![Image](http://learn.nextwork.org/blissful_yellow_calm_donkey/uploads/aws-devops-vscode_7a1de541)

---

## Using nano

An alternative to using IDEs is to directly edit files within the terminal. To edit index.jsp, I navigated to its directory within my EC2 instance and then ran the command nano index.jsp. This opened the file in nano, a built-in text editor that operates entirely within the terminal, allowing me to modify the code directly on the remote server.

Compared to using an IDE, editing index.jsp in the terminal felt more cumbersome due to the lack of visual aids, shortcuts, and advanced features like autocomplete or real-time syntax checking. I'd be more likely to use an IDE if I were working on complex projects, needed efficient navigation through multiple files, or prioritized a more comfortable and feature-rich coding experience. The terminal approach, while functional, is best suited for quick, minor edits or when an IDE is unavailable.

![Image](http://learn.nextwork.org/blissful_yellow_calm_donkey/uploads/aws-devops-vscode_a3324ad41)

---

---
