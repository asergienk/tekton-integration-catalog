# get-unreleased-bundle task

This task retrieves the highest bundle version from a specified package and channel in the provided FBC fragment. 
If package name and/or channel name are not specified, default values are used.
Default package name determination:
    
    * If there is only one 'olm.package', it's name is returned
    
    * If there are multiple 'olm.package' entries, the package with the highest bundle version in its 'defaultChannel' is selected
Default channel name determination:
    
    * The default channel name corresponds to the 'defaultChannel' entry of the selected package
The task checks whether the bundle is unreleased, specifically, not present in the Red Hat production Index Image (registry.redhat.io/redhat/redhat-operator-index). 
If the bundle is unreleased, the task returns it.
## Parameters
|name|description|default value|required|
|---|---|---|---|
|FBC_FRAGMENT|The FBC fragment image.||true|
|PACKAGE_NAME|The OLM package name.|If there is only one 'olm.package', it's name is returned. If there are multiple 'olm.package' entries, the package with the highest bundle version in its 'defaultChannel' is selected|false|
|CHANNEL_NAME|The OLM channel name.|The defaultChannel name for a given package.|false|

## Results
|name|description|
|---|---|
|unreleased-bundle|The name of the bundle that is not in registry.redhat.io/redhat/redhat-operator-index.|
