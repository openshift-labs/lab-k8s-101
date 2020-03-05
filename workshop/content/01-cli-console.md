## Command Line Interface

OpenShift includes both a command line tool, `oc` and a feature-rich web console with both an Administrator perspective and a Developer perspective. 

This lab environment has the `oc` command line tool installed, and your lab user is already logged in to the OpenShift cluster.

Issue the following command to see help information:

```execute-1
oc help
```

`oc` contains all the functionality of `kubectl`, plus some additonal OpenShift-specific features. You can use `kubectl` to interact with OpenShift if you choose, but these next sections will covers some of the additional features of `oc`.

### Using a Project

Projects are a top level concept to help you organize your deployments. An
OpenShift project allows a community of users (or a user) to organize and manage
their content in isolation from other communities. Each project has its own
resources, policies (who can or cannot perform actions), and constraints (quotas
and limits on resources, etc). 

In this lab environment, you already have access to single project: **%username%**.

If you had multiple projects, the first thing you would want to do is to switch
to the **%username%** project to make sure you're on the correct project from now on.
You can do this with the following command:

```execute-1
oc project %project_namespace%
```

## The Web Console

OpenShift ships with a web-based console that will allow users to
perform various tasks via a browser. In the Homeroom environment, the web console is embedded within the dashboard you are using to access the workshop.

To get a feel for how the web console works, switch to the web console by clicking on the **Console** tab or click here on this [Web Console](%console_url%) link.

The first time you access the web console, you will most likely be in the Administrator perspective. You will be presented with the list of Projects that you can access.

Click on the **%username%** project link. When you click on the
**%username%** project, you will be taken to the project details page,
which will list some metrics and details about your project. There's nothing there now, but that will change as you progress through the lab.

At the top of the left navigation menu, you can toggle between the Administrator perspective and the Developer perspective.


Select **Developer** to switch to the Developer perspective. Once the Developer perspective loads, you should be in the **Topology** view. Right now, there are no applications or components to view, but once you begin working on the lab, you'll be able to visualize and interact with the components in your application here.

