# Run as Docker Container
------

This is the simplest approach to get OneDev up and running. Idea for demonstration/concept-proof purpose. To do it, run below command in Linux environment:
```
docker run -it --rm -v /var/run/docker.sock:/var/run/docker.sock -v $(which docker):/usr/bin/docker -v /opt/onedev:/opt/onedev -p 6610:6610 1dev/server
```

Please note:

1.  Data will be kept in directory _/opt/onedev_, including database and repositories 
2.  Data will be migrated automatically when new release of OneDev image is used