# Service Files
This directory contains various build files and definitions for k8s deployment.

## Kubernetes deployment files

IMPORTANT: If you are planning to PR changes to deployment files, never ever
           directly modify files under kubernetes as these
           should get updated from templates/kubernetes during
           a maven build if profile `deploymentfiles` is enabled.
           After maven build has done updates, resulting changes
           can be PR'd.

To generate kubernetes deployment files from templates run command:

    ./mvnw process-resources -P deploymentfiles

CI build will use this profile during a release build so that
correct version are resolved from build properties and then
updated files will automatically land into git under correct
tag.

However with bamboo release process when next development version
is set these deployment files are kept on an older wrong version
as that particular step happens outside of a maven build. It can
either done manually after a release or get automated i.e. via
GitHub actions.
