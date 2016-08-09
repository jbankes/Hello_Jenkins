[![Build Status](http://ec2-52-43-46-166.us-west-2.compute.amazonaws.com:8080/job/Hello_Jenkins/badge/icon)](http://ec2-52-43-46-166.us-west-2.compute.amazonaws.com:8080/job/Hello_Jenkins/)

##Hello_Jenkins
This simple exercise is designed to introduce you to Jenkins and continuous
integration. This will be done in teams of 5 but we will all be working on one
Jenkins server.


###Overview
1. Fork the Repo.
2. Set up Job in Jenkins to connect to your repository and build c++ Hello_World.
3. Set up build status symbol.
4. Set up second job to run the program after build completes.

####Forking the repository
Someone on your team should hopefully has a Github account. Sign in to Github and navigate to www.github.com/jbankes/Hello_Jenkins. Go ahead and fork this repository and clone it to a computer.
To clone a repository using some Mac/Linux create run
```
$ git clone https://github.com/<your_Github_username>/Hello_Jenkins
```

####Setting up a Job in Jenkins
1. Navtigate to [Jenkins](http://ec2-52-43-46-166.us-west-2.compute.amazonaws.com:8080).
2. Click _New Item_.
3. Enter a name for your project, click _Freestyle Project_, then _OK_.
4. Set up _Source Code Management_.
  1. Select _git_.
  2. Enter the URL to your git repository
5. Setting up _Build Triggers_
  1. Select _Poll SCM_.
  2. Set up cron job by putting in `H/2 * * * *`.
6. Set up _Build_.
  1. Add build step _Execute Shell_.
  2. Enter `make` (This will run the Makefile).
7. Click _Save_.

####Set up _Embedded Build Status_ for Repo
The build status symbol often seen on a Github repository is normally connected
to TravisCI or JenkinsCI. We are using JenkinsCI which requires a plugin called
_Embedded Build Status_. I have already installed if for you. You just need to
add the proper information into you README.md file.

1. Open the README file in a text editor.
2. Go to the _Embedded Build Status_ page. The link is found on the main page of the job.
3. Select the _Markdown (with View) protected_ link and paste it in your README.
4. Commit your README changes and push to Github.
5. The change should automatically cause the job to build and after you can go to Github and check your repo. You should see the build status there

Because we selected _With View_ you will be able to click the build status icon which will take you to the Job in Jenkins.

####Set up Second Job to Run the Compiled Program
The final step to this demo is to set up a second job that automatically runs
after the project builds. This is different than the other job because this will
not have a git repository - it doesn't even build anything.

1. Create a new Job in Jenkins
  1. Click _New Item_.
  2. Enter a name for your second job, click _Freestyle Project_, then _OK_.
  3. Go immediately to build step and select _Execute Shell_.
  4. Enter the following Command `/var/lib/jenkins/workspace/<the name of your first project>/hello_exec`
  5. Save
2. Set your first job to call the second
  1. Go to your first job and open the _Configure_ page.
  2. Scroll to bottom and add a Post-Build Action. Select _Build other projects_.
  3. Enter your first job.
  4. Save
3. Run your first job
  1. After that successfully builds go and check your second job.
  2. You should see it successfully run.
  3. Select a Build Job from History and go to the console log to see your program output. If you program has run there then you successfully set up a basic pipeline.


###Wrapping it up
As you can see, Jenkins has a ton of opportunity which makes it the leading CI
tool for modern enterprise and software development. Jobs don't have to be
 explicitly build jobs which mean you can do other incredible things like deployments, promotions, testing, feedback, and much more. 
