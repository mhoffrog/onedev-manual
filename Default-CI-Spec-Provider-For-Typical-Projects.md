## Background

OneDev has built-in CI support to build projects. The build instructions are defined in _onedev-ci.xml_ in root of the project (do not worry about writing this xml, OneDev has visual editor to help you doing that). For some typical projects, it is possible that some default build instructions can be deducted automatically without existence of _onedev-ci.xml). Hence we added extension point [DefaultCISpecProvider](https://github.com/theonedev/onedev/blob/master/server-core/src/main/java/io/onedev/server/extensionpoint/DefaultCISpecProvider.java) to add support for different kinds of projects. 

## 

