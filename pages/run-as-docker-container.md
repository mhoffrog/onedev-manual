# Run as Docker Container
------

This is the simplest approach to get OneDev up and running. Idea for demonstration/concept-proof purpose. To do it, run below command in Linux environment:
```
docker run -it --rm -v /var/run/docker.sock:/var/run/docker.sock -v $(which docker):/usr/bin/docker -v $(pwd)/onedev:/opt/onedev -p 6610:6610 1dev/server
```

**NOTE:** The host path _$(pwd)/onedev_ will be used to store OneDev data, including database and repositories