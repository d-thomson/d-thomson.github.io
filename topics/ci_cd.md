# Continuous Integration & Continuous Delivery

## Introduction
Continuous integration is a DevOps software development practice where developers regularly merge their code changes into a central repository, after which automated builds and tests are run. Continuous integration most often refers to the build or integration stage of the software release process and entails both an automation component (e.g. a CI or build service) and a cultural component (e.g. learning to integrate frequently). The key goals of continuous integration are to find and address bugs quicker, improve software quality, and reduce the time it takes to validate and release new software updates.

In the past, developers on a team might work in isolation for an extended period of time and only merge their changes to the master branch once their work was completed. This made merging code changes difficult and time-consuming, and also resulted in bugs accumulating for a long time without correction. These factors made it harder to deliver updates to customers quickly.

With continuous integration, developers frequently commit to a shared repository using a version control system such as Git. Prior to each commit, developers may choose to run local unit tests on their code as an extra verification layer before integrating. A continuous integration service automatically builds and runs unit tests on the new code changes to immediately surface any errors.

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

[Sample.java](google.com)
[SampleTest.java](google.com)
[build.xml](google.com)

The Sample java file outputs "Hello, world!" to the console but also contains some methods that will be tested using some JUnit tests in the SampleTest.java file. First, navigate to the build job we previously created. Modify the Windows Batch command to first compile Sample.java then run it.

![](../img/run_cmd.PNG?raw=true "Changing the build job")

Next, we will enter the ant build.xml file in another step. Select **Add build step** then **Invoke Ant**. Enter the path to the build.xml file under the **Advanced** section.

![](../img/invoke_ant.PNG?raw=true "invoke ant")

Finally, we'll add a **Post build step** and specify our reporting XML files. For this, select Publish JUnit test result report under Post-build Actions. Enter `Reports/*.xml` in the Test report XMLs field.

![](../img/reporting.PNG?raw=true "reporting XMLs")

Finally, click save and click build now similar to the previous section. In the Build output information, you will now see a section named Test Result. Clicking into this, we'll see that we had 1 JUnit test fail. In the next section, we'll see an example of running automated tests from a build job.

#### Automated Testing
In this section we are going to set up an automated test. While setting up thi CI pipeline, the idea is that each build should be verifiable. In our example, if our unit tests pass, then subsequently UI tests should be run.

## Example
#### Part I
In this section, we will define a build job on a simple application and execute unit tests.

#### Part II
In this section, we will add some automated tests and a Jenkins pipeline.

## Tips, Tricks and Interview Questions
#### Tips & Tricks

#### Interview Questions

