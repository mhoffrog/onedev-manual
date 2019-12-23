Upgrade to any new OneDev versions can be done via below steps:

1. Assume OneDev is currently installed at _/path/to/onedev_, stop OneDev by running command _/path/to/onedev/bin/server.(sh|bat) stop_
1. Make sure database server is up and running if you are using external database
1. Extract new OneDev version to a separate folder, say _/path/to/new-onedev
1. Open a command window and change to directory _/path/to/new-onedev/bin_
1. Run command _./upgrade.(sh|bat) /path/to/onedev_ to perform the upgrade
1. _/path/to/onedev_ will be upgraded and you may launch it to check if things are in order
1. You may remove _/path/to/new-onedev_ afterwards if everything is fine
