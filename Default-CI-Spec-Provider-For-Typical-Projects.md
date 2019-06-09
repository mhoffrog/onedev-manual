# Background

OneDev has built-in CI support to build projects. The build instructions are defined in _onedev-ci.xml_ in root of the project (do not worry about writing this xml, OneDev has visual editor to help you doing that). For some typical projects, it is possible that some default build instructions can be deducted automatically without existence of _onedev-ci.xml_. Hence we introduced extension point [DefaultCISpecProvider](https://github.com/theonedev/onedev/blob/master/server-core/src/main/java/io/onedev/server/extensionpoint/DefaultCISpecProvider.java) to support different kinds of projects via plugins, and want you to help writing such plugin.

# Pre-requisite

### Familiar with Java

OneDev is written in Java, and familiar with Java is a must. 

### Application frameworks knowledge

To write such plugin, you will need to be familiar with some application frameworks, especially its underlying build/test mechanism. For instance, Spring project in Java world normally contains a file _pom.xml_ under the project root, and it means that the project can be built/test with Apache Maven by calling _mvn clean test_. So the [maven plugin](https://github.com/theonedev/onedev/tree/master/server-plugin/server-plugin-maven) checks existence of _pom.xml_ and parses this file to help generating the default CI spec if it exists.

### Docker knowledge

Different projects may require different environments to build and test. OneDev relies on [docker](https://www.docker.com/) to solve this issue. When provide default CI spec for a particular project, you will need to decide which docker image to use by analyzing the project files. 

# Write the plugin

Please follow [this guide](Develop-Built-In-Plugins) to prepare development environment. You may check [maven plugin](https://github.com/theonedev/onedev/tree/master/server-plugin/server-plugin-maven) to see how we provide default CI spec for Maven projects. 

It is suggested to develop the plugin on Linux which is more docker friendly. However you can still 