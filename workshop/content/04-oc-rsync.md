## Live Development

If you want to test changes **before** you commit, one way to do that is with the `oc rsync` command.

Make a minor edit to your local repo's `index.html` file, then test your changes before you commit by synching content into your hosted container:

```execute-1
export PODNAME=$(oc get pods -l app=http-base | tail -n 1 | cut -f1 -d' ')
oc rsync -w --exclude='.git,node_modules' . $PODNAME:
```

If you reload the application in the browser, you should see the change.

For another way to do fast, iterative development on OpenShift, you can learn about `odo` in the next section.
