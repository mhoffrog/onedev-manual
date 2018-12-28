To fix issue via commit message, use the syntax 
```
[fix|fixed|fixes|resolve|resolved|resolves] #<issue number>
```
For instance, `fix #123`

This way, issue is associated with commit, and OneDev leverages this information to provide below functionalities:
1. List all issues fixed in a certain build
1. List all issues fixed between two builds
1. List commits included in a certain build
1. List commits included between two builds
1. List commits including fix of particular issue
1. List builds including fix of particular issue
1. List pull requests including fix commits of particular issue