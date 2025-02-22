![CoreMedia Labs Logo](https://documentation.coremedia.com/badges/banner_coremedia_labs_wide.png "CoreMedia Labs Logo")

![CoreMedia Content Cloud Version](https://img.shields.io/static/v1?message=2104&label=CoreMedia%20Content%20Cloud&style=for-the-badge&labelColor=666666&color=672779 
"This badge shows the CoreMedia version this project is compatible with. 
Please read the versioning section of the project to see what other CoreMedia versions are supported and how to find them."
)
![Status](https://img.shields.io/static/v1?message=active&label=Status&style=for-the-badge&labelColor=666666&color=2FAC66 
"The status badge describes if the project is maintained. Possible values are active and inactive. 
If a project is inactive it means that the development has been discontinued and won't support future CoreMedia versions." 
)


# Displaying Feedback with the CoreMedia Feedback Hub 

## Overview 

In this tutorial you will learn about how to use the CoreMedia Feedback Hub API.
It explains step-by-step how to set up a new CoreMedia Extension for the Feedback Hub
and how to build a new Feedback Hub adapter or provider with the
corresponding classes, localization, error handling, etc.

## Versioning

To find out which CoreMedia versions are supported by this project, 
please take look at the releases section or on the existing branches. 
To find the matching version of your CoreMedia system, please checkout the branch 
with the corresponding name. For example, 
if your CoreMedia version is 2104.1, checkout the branch 2104.1.



## How To Read This Tutorial

There are two possibilities to implement your Feedback Hub adapter, depending
on your use case. This tutorial covers both cases in separate sections: 

**FeedbackHubAdapter**
 
The Feedback Hub has predefined `FeedbackHubAdapters`. They offer some prefabrication
to make the integration of similar services easier. One example for this
is the `BlobKeywordsFeedbackHubAdapter` which already gives us the data blob the keywords 
should be extracted from. Please check the documentation for the list of existing
`FeedbackHubAdapters`. 

Tutorial Link: **[Implementing a FeedbackAdapter](example_adapter.md)**

**FeedbackProvider**

The `FeedbackProvider` interface is the general interface to implement for any
kind of feedback. It does not offer any kind of prefabrication and can be used
if none of the existing `FeedbackHubAdapters` are applicable for your use case.

Tutorial Link: **[Implementing a FeedbackProvider](example_provider.md)**


## Getting Started

This repository is a plugin for the CoreMedia Blueprint workspace.
To include it, perform the following steps:

- clone this project
- build it via `mvn clean install`


#### Studio Server Development

To debug the Java code of you plugin, start the Studio Server of your CoreMedia Blueprint
workspace in __debug__ mode and pass the testsystem host name and the location
of the plugin directory where the zip archive of this plugin is located.
For example: 

`mvnDebug spring-boot:run -Dinstallation.host=my-test-system.vm -Dplugins.directories=C:/workspace/plugins`

Afterwards, create a "Remote Debug" configuration in IDEA with transport `Socket`,
host `localhost` and port `8000`. The VM parameter should look like this:

`-agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=*:8000`

In IDEA, it should look like this:

![Feedback Rendering](images/debugging.png "IDEA Debug Configuration")

When executed, the Studio server will start up and you will be able to 
debug your plugin.


#### Studio Client Development

- When you have a CoreMedia test system where the Java module of this plugin is already deployed
or this plugin does not have any Java plugin modules, just invoke the following command
from the root directory of your CoreMedia Blueprint workspace: 

```
mvn jangaroo:run -pl :studio-resources -Dinstallation.host=<YOUR_TEST_SYSTEM_HOST>
```

- If you want to use your local Studio server, start the Studio server
and invoke the following command from the root directory of the CoreMedia Blueprint workspace:

```
mvn jangaroo:run -pl :studio-resources -DadditionalPackagesDirs=<BASE_DIR>/feedback-hub-adapter-tutorial/studio-client/target/app
```

The parameter `installation.host` is not required here, since we are working 
with a local Studio server. Note that the parameter `additionalPackagesDirs` accepts 
multiple folders from different apps in a comma separated format.
This allows you to develop multiple plugins in parallel.

Finally, login to the Studio at URL http://localhost:8080.
    

## CoreMedia Labs

Welcome to [CoreMedia Labs](https://blog.coremedia.com/labs/)! This repository
is part of a platform for developers who want to have a look under the hood or
get some hands-on understanding of the vast and compelling capabilities of
CoreMedia. Whatever your experience level with CoreMedia is, we've got something
for you.

Each project in our Labs platform is an extra feature to be used with CoreMedia,
including extensions, tools and 3rd party integrations. We provide some test
data and explanatory videos for non-customers and for insiders there is
open-source code and instructions on integrating the feature into your
CoreMedia workspace. 

The code we provide is meant to be example code, illustrating a set of features
that could be used to enhance your CoreMedia experience. We'd love to hear your
feedback on use-cases and further developments! If you're having problems with
our code, please refer to our issues section. If you already have a solution to 
an issue, we love to review and integrate your pull requests. 

