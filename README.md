[![Build Status](http://ec2-52-43-46-166.us-west-2.compute.amazonaws.com:8080/job/Hello_Jenkins/badge/icon)](http://ec2-52-43-46-166.us-west-2.compute.amazonaws.com:8080/job/Hello_Jenkins/)

##Hello_Jenkins
![Jenkins Overview](https://github.com/jbankes/Hello_Jenkins/img/jenkins_overview.png "Jenkins Overview")
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


####Set up Second Job to Run the Compiled Program
