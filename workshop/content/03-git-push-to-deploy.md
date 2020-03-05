## Background: Webhooks

Most Git repository servers support the concept of webhooks -- calling to an
external source via HTTP(S) when a change in the code repository happens.
OpenShift provides an API endpoint that supports receiving hooks from
remote systems in order to trigger builds. By pointing the code repository's
hook at the OpenShift API, automated code/build/deploy pipelines can be
achieved.

## Clone a Local Copy of Your Fork
Clone a local copy of your fork:
```copy-and-edit
git clone https://github.com/YOUR_GITHUB_USER/http-base
```

Then `cd` to the directory:

```execute-1
cd http-base
```

## Configuring GitHub Web Hooks
In this section you can use a build webhook to trigger a new build any time there is a change to your repository. In the the Developer perspective in the web console, click **Builds** in the left navigation. Click the `http-base` build config and scroll down to the Webhooks section.

There will be two entries in the Webhooks section. The GitHub webhook is the one we are interested in.

Click **Copy URL with Secret** for the GitHub webhook. Once you have the URL copied to your clipboard, navigate to your forked github repo.

Click the **Settings** link on the top right of the page.

Click on **Webhooks**, then the **Add Webhook** button

In the next screen, paste your link into the "Payload URL" field. You can leave the
secret token field blank -- the secret is already in the URL.

**NOTE**: If the URL you paste contains `kubernetes.default.svc`, it will need to be modified - contact one of the instructors.

Change the `Content Type` to `application/json`.

Finally, click on **Add Webhook**.

Now, each time you commit new source code to your GitHub
repository, a new build and deployment will occur inside of OpenShift.  Let's try
it out.

## Using GitHub Webhooks
Make a small change to the index.html file, either in an editor or in the GitHub web interface. For example, you can change the H1 tag from 

```
<h1>HTTP-base on OpenShift</h1>
```

to something else, such as 

```
<h1>Hello OpenShift!</h1>
```

Commit and push your changes.


Once you have done that, a **Build** should almost instantaneously be
triggered in OpenShift. From the **Topology** page, click the circle for `http-base` and look at the **Builds** section of the **Resources** tab, or, run the
following command to verify:

```execute-1
oc get builds
```

You should see that a new build is running:

```
NAME          TYPE      FROM          STATUS     STARTED          DURATION
http-base-1   Source    Git@b052ae6   Complete   17 minutes ago   1m27s
http-base-2   Source    Git@3b26e1a   Running    6 seconds ago
```

Once the build and deploy has finished, verify your new image was
automatically deployed by viewing the application in your browser.

You should now see the new H1 tag on the page.
