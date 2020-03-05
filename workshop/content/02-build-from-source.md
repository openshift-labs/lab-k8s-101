## Source-to-Image

Source-to-Image combines source repos and operationally-maintained builder images to produce application images. It's included with OpenShift and is also available as a standalone project, for use with Jenkins or other external builder processes: [Source-to-Image](https://github.com/openshift/source-to-image)

## Fork the Repo

For this section, we'll deploy a fork of the **ryanj/http-base** repository.

Fork the https://github.com/ryanj/http-base repository. This will allow you to configure your own GitHub webhooks in a later section.

```copy
https://github.com/ryanj/http-base
```

## Deploy from the Web Console

There are multiple ways to deploy applications. We'll start by deploying a simple application via the Developer Perspective in the web console. In the [web console](%console_url%) toggle back to the Developer Perspective if necessary.

Click **From Git** on the **Topology** page or click the **+Add** item in the left navigation and then choose **From Git**. Enter the URL for your fork:

```copy-and-edit
https://github.com/YOUR_GITHUB_USER/http-base
```

Select **Node.js** and leave version 10 selected by default, then click **Create**.

You'll be directed back to the **Topology** page, where you can see the status of the deployment. If you click the build status icon in the bottom left corner of the `http-base` deployment, you'll be able to view the build logs. Click **Topology** in the left navigation to return to the Topology page.

Once the build is complete and the circle around the `http-base` component turns blue, click the Open URL icon in the top right corner of the `http-base` deployment to open the URL in your browser. 

## Deploy from the Command Line

While we used the web console to deploy the application, you could have done it using the command line. Don't execute this, since you've already deployed it, but here is the command you could have run:

```
oc new-app https://github.com/YOUR_GITHUB_USER/http-base
```

That command is telling OpenShift that we want to create an application based on the source code in that git repository. Source-to-image will infer that this is a Node.js application and will use the appropriate builder image.

When you create an application using `oc new-app` it doesn't create a Route (publicly accessible URL) automatically. To expose the service and create a Route, you would use this command:

```
oc expose svc/http-base
```

Now you know two ways to deploy an application: with the web console and with the command line. Next you'll learn how to set up git webhooks so that any new changes to your code trigger a new build and deployment. 

