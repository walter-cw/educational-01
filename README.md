# Hands-on Jenkins-02 : Creating first Jenkins Job on Amazon Linux 2 AWS EC2 Instance

Purpose of the this hands-on training is to teach the students how to create Jenkins jobs on Amazon Linux 2 EC2 instance.

## Learning Outcomes

At the end of the this hands-on training, students will be able to;

- create Jenkins Jobs on Amazon Linux 2 EC2 instance

## Outline

- Part 1 - Launch Amazon Linux 2 EC2 Instance and Connect with SSH

- Part 2 - Install Jenkins on Amazon Linux 2 EC2 Instance

- Part 3 - Open Jenkins dashboard and explain plugins and other jenkins menu elements

- Part 4 - Create first Jenkins Job

## Part 1 - Launch Amazon Linux 2 EC2 Instance and Connect with SSH

- Launch an EC2 instance using the Amazon Linux 2 AMI with security group allowing SSH connections.

- Connect to your instance with SSH.

```bash
ssh -i .ssh/call-training.pem ec2-user@ec2-3-133-106-98.us-east-2.compute.amazonaws.com
```

## Part 2 - Install Jenkins on Amazon Linux 2 EC2 Instance using Docker

- Launch an AWS EC2 instance of Amazon Linux 2 AMI with security group allowing SSH and Tomcat 
(8080) ports and name it as `call-jenkins` 

- Connect to the `call-jenkins` instance with SSH.

```bash
ssh -i .ssh/call-training.pem ec2-user@ec2-3-133-106-98.us-east-2.compute.amazonaws.com
```

- Update the installed packages and package cache on your instance.

```bash
sudo yum update -y
```

- Install the most recent Docker Community Edition package.

```bash
sudo amazon-linux-extras install docker -y
```

- Start docker service.

```bash
sudo systemctl start docker
```

- Enable docker service so that docker service can restart automatically after reboots.

```bash
sudo systemctl enable docker
```

- Check if the docker service is up and running.

```bash
sudo systemctl status docker
```

- Add the `ec2-user` to the `docker` group to run docker commands without using `sudo`. 

```bash
sudo usermod -a -G docker ec2-user
```

- Normally, the user needs to re-login into bash shell for the group `docker` to be effective, but `newgrp` command can be used activate `docker` group for `ec2-user`, not to re-login into bash shell.

```bash
newgrp docker
```

- Check the docker version without `sudo`.

```bash
docker version
```

- Run docker jenkins image from Dockerhub Jenkins.

```bash
docker run \
  -u root \
  --rm \
  -d \
  -p 8080:8080 \
  -p 50000:50000 \
  --name jenkins \
  -v jenkins-data:/var/jenkins_home \
  -v /var/run/docker.sock:/var/run/docker.sock \
  jenkins/jenkins:lts
```

- Get the administrator password from `var/jenkins_home/secrets/initialAdminPassword` file.

```bash
docker exec -it jenkins bash
cat /var/jenkins_home/secrets/initialAdminPassword
exit
```

- The administrator password can also be taken from docker logs 

```bash
docker logs jenkins
```

- Enter the temporary password to unlock the Jenkins
 
- Install suggested plugins
 
- Create first admin user (call-jenkins:Call-jenkins1234)
 
- Check the URL, then save and finish the installation

## Part 3 - Open Jenkins dashboard and explain plugins and other jenkins menu elements

- Open plugins menu and download some plugins,

- Explain Items tab at menu

- Explain Manage Jenkins tab at menu

- Explain other Jenkins terminology

## Part 4 - Create First Jenkins Job on Amazon Linux 2 EC2 Instance


- In this handson we will create a job in Jenkins which picks up a simple "Hello World" python script, builds and runs the python code. Our example will be very simple but you can manage complex applications.

- The freestyle build job is a highly flexible and easy-to-use option. You can use it for any type of project; it is easy to set up, and many of its options appear in other build jobs.

* To create a Jenkins freestyle job, open your Jenkins installation path. It will be hosted on <b>http://localhost:8080</b> or <b>http://ec2-ip-address:8080</b> If you have installed to different port, please use this port number. Then log on to your Jenkins dashboard with username and password.


* Open your Jenkins dashboard and click on <b>New Item</b> to create a new item.




* Enter the <b>item name</b> then select <b>free style project</b> and click to <b>OK</b>.


```
While creating first Project you will see four tab. These are:

1. Source Code Management Tab : optional SCM, such as CVS or Subversion where your source code resides.
2. Build Triggers : Optional triggers to control when Jenkins will perform builds.
3. Build Environment: Some sort of build script that performs the build (ant, maven, shell script, batch file, etc.) where the real work happens
4. Build : Optional steps to collect information out of the build, such as archiving the artifacts and/or recording javadoc and test results.
5. Post-build Actions : Optional steps to notify other people/systems with the build result, such as sending e-mails, IMs, updating issue tracker, etc.
```

* Specify your Jenkins project's <b>description</b>. Then go to <b>Build</b>.





* Choose appropriate build step from "Add build step". It depends on your operating system.  If you are windows user you can choose <b>Execute Windows batch command</b> or if you are using  Linux or MacOS operating system, you can choose <b>Execute shell</b>.





* When you select the build step, command space will be shown. Write down just <b>echo "Hello World"</b> to execute shell command/windows batch command.





* Then click **apply**  and **save**  button.

* After that you will see inside of the Project. Then click to <b>Build now</b> and wait e few seconds. You will see result of this build action under the **Build History**





* As we mentioned above you will see the results of the build. If you click to the build number, you can reach build page. If you see the number blue that means build worked well.





* From build page you can see console results from "Console Output".





* You can see results of your build. As you can see our result our job printed out to "Hello World" and it finished with "SUCCESS".



