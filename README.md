Accelerated Build Now Plugin
============================
The Jenkins Accelerated Build Now Plugin allows Jenkins users to launch a project's build right away, even if the queue is long (moving it to the top of the queue) but without killing off jobs if no executor is available.

## How to build and test :
Simply clone this repo and run mvn clean install hpi:run

## How to install :
Download the [latest release](https://github.com/florian-besser/accelerated-build-now-plugin/releases) and use Jenkins installer advanced tab to upload and install it to Jenkins.

## How to use :
When your Jenkins cluster is overloaded with jobs (for example a queue with 10+ builds, all the executors busy with nightly builds that take ages), you know you will wait ages before the job you want to run effectively starts running.
Relax ! With the Accelerated Build Now Plugin, your job will get scheduled with top priority !

1. The queue is full of automatically (not user launched) scheduled jobs, and the only executor available is busy ...

![Screenshot](https://raw.github.com/Terracotta-OSS/accelerated-build-now-plugin/gh-pages/screenshots/queue_is_long.png "A long queue to wait for")

2. You want your job maven-surefire to run ASAP, so you click on the Accelerated Build Now button

![Screenshot](https://raw.github.com/Terracotta-OSS/accelerated-build-now-plugin/gh-pages/screenshots/accelerated_button.png "Accelerated Build Now !")

3. Your maven-surefire job just got priorized to the top of the queue and will start running as soon as the next executor becomes available.

4. A nice rhyno badge was added to your build that got "acceleratedly built".

## How does that work ?
When you click on the Accelerated Build Now button, the plugin will :
* make sure the queue is not empty and all the excutors are busy ( if not, it will normally schedule the build and exit)
* sort the queue using a QueueSorter wrapping any existing QueueSorter (such as the Priority Sorter Plugin queue sorter)

## Authors :
This plugin was developed by Terracotta, by

- [Anthony Dahanne](https://github.com/anthonydahanne/)

It was then forked and the feature to kill builds removed, by

- [Florian Besser](https://github.com/florian-besser/)

## License
Apache 2 licensed (see LICENSE.txt)
