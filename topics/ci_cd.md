# Continuous Integration & Continuous Delivery

## Introduction
Continuous integration and Delivery is a development practice where developers frequently merge code changes into a central repository,  and after each merge, automated builds, tests and deployments are executed. Continuous Integration refers to the building and integration phase of the software release process. This involves an automation service, such as Jenkins or Travis CI, that performs the build and tests automatically. The key goals of Continuous Integration are to quickly find defects, improve quality, and reduce the time it takes to validate and release new software updates.

In the past, teams may work in silos for an extended period of time then merge changes once their work was completed. This made merging code changes difficult and time-consuming, and often resulted in [merge hell](https://xkcd.com/1597/). This made it harder to deliver updates quickly.

With continuous integration, commits to a shared repository using a using version control, git for example, are done frequently. Prior to each commit, developers may choose to run local unit tests on their code as an extra verification layer before integrating. A continuous integration service automatically builds and runs unit tests on the new code changes to immediately surface any errors.

With continuous delivery, code changes are automatically built, tested, and prepared for a release to production. Continuous delivery expands upon continuous integration by deploying all code changes to a testing environment and/or a production environment after the build stage.

## Tutorial
Below is a short tutorial on the Jenkins CI/CD tool. Jenkins is an open source tool and considered a standard in continuous integration. This tutorial was written using the Windows architecture with Java as the domain-specific language.

#### Setup
The first thing you should do before getting started with Jenkins is download and install it. Installers for various platforms can be found in the link below.

[Download Jenkins](https://jenkins.io/download/)

Once installed, your browser should open to the Jenkins UI. The default address will be `localhost:8080`. For the first time setup you will be walked through some initial confiruations. Note that default keys, such as the admin password, will be stored in `<Jenkins Install Dir>/secrets`.

#### Build Jobs
The first step to working with Jenkins is to create a build job. To do so, select **New Item** from the menu on the left side of Jenkins UI. Enter a name for the item, in this example Tutorial Build Job was entered, and select **Freestyle Project**. Click OK at the bottom of the page.

![](../img/new_build_job.png?raw=true "Adding a new build job")

Next, the configuration page for the freestyle Jenkins job will show. There are a number of confuration parameters available to this job type such as build triggers, build environments and post-build actions. For this tutorial, we are only concerned with adding a build step. Add some text to the description of this job and navigate to the bottom of the page to the **Build** section. Select the build drop-down and select the Execute Windows batch command option. You'll see that a **command** window appears, this allows us to enter anyt batch commands we wish to execute as a part of this Jenkins freestyle job. For this example, we want to get the Java version on the executing machine as well as the working directory listing.

![](../img/add_build_step.PNG?raw=true "Adding a new build step to the Job")

Once entered, click save, this will commit our changes for this freestyle job and take us to the jobs landing page. If you navigate back to the Jenkins homepage, you'll notice your job will be displayed there also. Next we will actually run this job. On the build jobs landing page, select the build now button.

![](../img/build_now.png?raw=true "Build now")

When clicked, the build job with begin. You'll notice an entry will appear in the build history box. Click on the job and select **console output**. 

![](../img/console_output.PNG?raw=true "View the console output of the build job")

On this page, you will see the results of the commands that we specified in our job.

![](../img/console_output_text.PNG?raw=true "The console output of the build job")

This is important since we can see from here where Jenkins is installed and where our executions are running. In the next section, we'll deploy a small Java program and run unit tests from Jenkins.

#### Unit Testing
As mentioned earlier, Jenkins offers and also ships with many plugins. The one in particular for this section is JUnit. We will be using Jenkins to kick off our unit tests for some Sample Java files. First, download the two Java files and build file below and place them in `<Jenkins Install Dir>/workspace/Tutorial Build Job`, also create a `Reports` directory where we will store our output. If you are unsure of this location, check the console output from the previous section, it will be located in the console output of the build job.

The Sample java file outputs "Hello, world!" to the console but also contains some methods that will be tested using some JUnit tests in the SampleTest.java file. First, navigate to the build job we previously created. Modify the Windows Batch command to first compile Sample.java then run it.

![](../img/run_cmd.PNG?raw=true "Changing the build job")

Next, we will enter the ant build.xml file in another step. Select **Add build step** then **Invoke Ant**. Enter the path to the build.xml file under the **Advanced** section.

![](../img/invoke_ant.PNG?raw=true "invoke ant")

Finally, we'll add a **Post build step** and specify our reporting XML files. For this, select Publish JUnit test result report under Post-build Actions. Enter `Reports/*.xml` in the Test report XMLs field.

![](../img/reporting.PNG?raw=true "reporting XMLs")

Finally, click save and click build now similar to the previous section. In the Build output information, you will now see a section named Test Result. Clicking into this, we'll see that we had 1 JUnit test fail. In the next section, we'll see an example of running automated tests from a build job.

## Test
Now that you have completed the tutorial, complete the following tasks:
1. Download and set up a private jenkins server.
2. Add a build job and run it. This build job can be a simple Java program
3. Set up junit tests within your program 
4. Add a post build step to generate reports based off the unit tests.


## Tips, Tricks and Interview Questions
* Define a typical use case of Jenkins

Using pipelines to test a pull request. This helps speed up the code review process drastically and helps find bugs quickly.

* What advantages does using Jenkins offer?

Code changes are automatically built, tested, and prepared for a release to production. This automates the dev ops side of things and speeds up integration testing drastically.

* What is the purpose of a plugin?

Plugins are used to enhance Jeknins usability and integrate with various technologies. They are mostly developed by the community and open source. 

* What is the difference between continuous integration and continuous delivery?

With continuous delivery, code changes are automatically built, tested, and prepared for a release to production. Continuous delivery expands upon continuous integration by deploying all code changes to a testing environment and/or a production environment after the build stage.
