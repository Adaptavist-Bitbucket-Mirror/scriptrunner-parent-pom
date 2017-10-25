# ScriptRunner script plugins - base poms

This is the hierarchy of parent poms on which ScriptRunner script
plugins can be a based.

It consists of a top-level **scriptrunner-base** pom which declares
common _properties_, _dependencyManagement_ and _build/pluginManagement_
sections.

Under which are a set of per Atlassian product base poms which
declare the product specific sections as above:

* **scriptrunner-bamboo-base**
* **scriptrunner-bitbucket-base**
* **scriptrunner-confluence-base**
* **scriptrunner-jira-base**

Note: These don't specify the dependencies or build plugins directly
though, allowing them to be used as a lower level base if necessary.

On top of these sits the standard dependency & build poms - these are
the ones that we expect most plugins will inherit from:

* **scriptrunner-bamboo-std**
* **scriptrunner-bitbucket-std**
* **scriptrunner-confluence-std**
* **scriptrunner-jira-std**

They provide recommended *dependencies* and *build/plugins* pom sections
so that user plugin poms can be kept as simple as possible.

## Updating from scriptrunner-parent

These poms have a different groupId and artifactId pattern to avoid
blindly updating from the old scriptrunner-parent pom.

Plugins wishing to use the new poms will need to select the appropriate
product specific standard pom as their new parent.

eg:

    <parent>
        <groupId>com.adaptavist.pom</groupId>
        <artifactId>scriptrunner-jira-standard</artifactId>
        <version>8</version>
    </parent>
