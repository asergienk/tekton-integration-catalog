# get-unreleased-bundle stepaction

This StepAction identifies unreleased bundles—those not present in the Red Hat production Index Image (registry.redhat.io/redhat/redhat-operator-index)—and determines the appropriate package, channel, and bundle for testing.
    
    - If all unreleased bundles belong to the same package, that package will be used for testing.

    - If they belong to different packages, user input is required; the PACKAGE_NAME parameter must be set by the user.
    
    - If multiple unreleased bundles exist within the same package, the highest bundle version is selected.
    
    - If CHANNEL_NAME is not provided, the 'defaultChannel' of the package is used.
    
    - If no unreleased bundles are found, the step exits without performing further actions.

This StepAction ultimately determines and returns a single unreleased bundle.
## Parameters
|name|description|default value|required|
|---|---|---|---|
|fbcFragment|A FBC fragment image.||true|
|packageName|An OLM package name present in the fragment or leave it empty so the step will determine the default package name as described above.|""|false|
|channelName|An OLM channel name or leave it empty so the step will determine the default channel name as described above.|""|false|

## Results
|name|description|
|---|---|
|unreleasedBundle|The name of the bundle that is not in registry.redhat.io/redhat/redhat-operator-index.|
