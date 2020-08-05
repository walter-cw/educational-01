In this handson we will create a job in Jenkins which picks up a simple "Hello World" python script, builds and runs the python code. Our example will be very simple but you can manage complex applications.

The freestyle build job is a highly flexible and easy-to-use option. You can use it for any type of project; it is easy to set up, and many of its options appear in other build jobs.

 1 - To create a Jenkins freestyle job, open your Jenkins installation path. It will be hosted on <b>http://localhost:8080</b> or <b>http://ec2-ip-address:8080</b> If you have installed to different port, please use this port number. Then log on to your Jenkins dashboard with username and password.

<center><img src="https://media.clarusway.com/Jenkins/3-1-1-1-browser.png"></center>

<div class="alert alert-success" role="alert">  
2 - Open your Jenkins dashboard and click on <b>New Item</b> to create a new item.
</div>
|<center><img src="https://media.clarusway.com/Jenkins/3-1-2-create-a-new-item.png" class="img-fluid" alt=""></center>|
|:--:|
|*Create new item*|

<div class="alert alert-success" role="alert">  
3 - Enter the <b>item name</b> then select <b>free style project</b> and click to <b>OK</b>.
</div>

|<center><img src="https://media.clarusway.com/Jenkins/3-2-2.png" class="img-fluid" alt=""></center>|
|:--:|
|*Create project*|

While creating first Project you will see four tab. These are:

1. Source Code Management Tab : optional SCM, such as CVS or Subversion where your source code resides.
2. Build Triggers : Optional triggers to control when Jenkins will perform builds.
3. Build Environment: Some sort of build script that performs the build (ant, maven, shell script, batch file, etc.) where the real work happens
4. Build : Optional steps to collect information out of the build, such as archiving the artifacts and/or recording javadoc and test results.
5. Post-build Actions : Optional steps to notify other people/systems with the build result, such as sending e-mails, IMs, updating issue tracker, etc.

<div class="alert alert-success" role="alert">  
4 - Specify your Jenkins project's <b>description</b>. Then go to <b>Build</b>.
</div>

|<center><img src="https://media.clarusway.com/Jenkins/3-+description.png" class="img-fluid" alt=""></center>|
|:--:|
|*Description*|

<div class="alert alert-success" role="alert">  
5 - Choose appropriate build step from "Add build step". It depends on your operating system.  If you are windows user you can choose <b>Execute Windows batch command</b> or if you are using  Linux or MacOS operating system, you can choose <b>Execute shell</b>.
</div> 

|<center><img src="https://media.clarusway.com/Jenkins/3-build.png" class="img-fluid" alt=""></center>|
|:--:|
|*Add build step*|

<div class="alert alert-success" role="alert">  
6 - When you select the build step, command space will be shown. Write down just <b>echo "Hello World"</b> to execute shell command/windows batch command.
</div> 

|<center><img src="https://media.clarusway.com/Jenkins/jenkins-build-command.png" class="img-fluid" alt=""></center>|
|:--:|
|*Build Command*|

<div class="alert alert-success" role="alert">  
7 - Then click <b>apply</b>  and <b>save</b>  button.
</br></br>
8 - After that you will see inside of the Project. Then click to <b>Build now</b> and wait e few seconds. You will see result of this build action under the <b>Build History</b>
</div> 

|<center><img src="https://media.clarusway.com/Jenkins/3-build-now.png" class="img-fluid" alt=""></center>|
|:--:|
|*Add build step*|

<div class="alert alert-success" role="alert">  
9 - As we mentioned above you will see the results of the build. If you click to the build number, you can reach build page. If you see the number blue that means build worked well.
</div> 

|<center><img src="https://media.clarusway.com/Jenkins/3-build-history.png" class="img-fluid" alt=""></center>|
|:--:|
|*Click the build number*|

<div class="alert alert-success" role="alert">  
10 - From build page you can see console results from "Console Output".
</div> 

|<center><img src="https://media.clarusway.com/Jenkins/3-console-output1.png" class="img-fluid" alt=""></center>|
|:--:|
|*Build Page*|

<div class="alert alert-success" role="alert">  
11 - You can see results of your build. As you can see our result our job printed out to "Hello World" and it finished with "SUCCESS".
</div> 

|<center><img src="https://media.clarusway.com/Jenkins/3-console-output.png" class="img-fluid" alt=""></center>|
|:--:|
|*Console Output*|
