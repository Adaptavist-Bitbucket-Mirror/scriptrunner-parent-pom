# ScriptRunner script plugin parent poms

If you want to build a ScriptRunner-based plugin, this project
has the parent pom that you can inherit from to build your plugin.

For most users, you want the product-specific standard parent pom.
This will be one of the following, depending on your host application:

* **scriptrunner-bitbucket-standard**
* **scriptrunner-confluence-standard**
* **scriptrunner-jira-standard**

Those are the "batteries and the kitchen sink included" poms. They'll
let you keep your script plugin's pom as simple as possible, getting 
out of your way so that you can focus on the scripting.

# Underlying hierarchy
Okay, so what about the other poms in this repository? There is a 
hierarchy of parent poms on which ScriptRunner projects may be
based.

At the top-level sits the **scriptrunner-base** pom which declares
common _properties_, common _dependencies_ and _build/pluginManagement_
sections.

Under this are a set of per Atlassian product base poms which
declare the product specific sections as above:

* **scriptrunner-bitbucket-base**
* **scriptrunner-confluence-base**
* **scriptrunner-jira-base**

Within those base projects are the build poms. These are the poms that we expect most plugins will 
inherit from and where product specific dependencies needed for compilation are listed.

* **scriptrunner-bitbucket-standard**
* **scriptrunner-confluence-standard**
* **scriptrunner-jira-standard**

They provide recommended *dependencies* and *build/plugins* pom sections
so that user plugin poms (scriptrunner-samples) can be kept as simple as possible.

## Updating from scriptrunner-parent

These poms have a different groupId and artifactId pattern to better
indicate their nature and to avoid blindly updating from the old 
scriptrunner-parent pom.

Plugins wishing to use the new poms will need to select the appropriate
product specific standard pom as their new parent, and probably
rip out large swaths of their configuration.

eg:

    <parent>
        <groupId>com.adaptavist.pom</groupId>
        <artifactId>scriptrunner-jira-standard</artifactId>
        <version>8</version>
    </parent>