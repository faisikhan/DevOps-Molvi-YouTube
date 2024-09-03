# 50+ Docker Commands for DevOps Engineers

1. sudo systemctl status docker  ==============>>  Check the status of the Docker Engine
2. sudo systemctl enable docker    ==============>>  to start docker on boot automatically.
3. sudo systemctl start docker  ==============>>  It will start the Docker Engine
4. sudo systemctl stop docker    ==============>> It will stop the Docker Engine
5. sudo systemctl restart docker  ==============>>  It will restart the Docker Engine
6. docker version   ==============>> You can check the version of Docker Engine
7. docker info  ==============>> Shares all the information about Docker infra,version, storage etc.
8. docker search ubuntu  ==============>> It will search the Ubuntu image
9. docker pull ubuntu  ==============>> pulls the Ubuntu image on your host
10. docker images  ==============>> shows all Docker images on the system
11. docker rmi ubuntu  ==============>> removes the image
12. docker rmi ubuntu:24.04  ==============>> removes the image with a specific tag
13. docker rmi -f hello-world  ==============>> forcefully removes the image
14. docker run ubuntu  ==============>>  runs the Ubuntu image into a container
15. docker run nginx  ==============>> it runs the NGINX container
16. docker run -it -d nginx  ==============>> the container will run in the foreground
17. docker ps  ==============>> shows the running containers
18. docker ps -a  ==============>> shows all containers running + Exit state
19. docker container ls  ==============>> shows the running containers
20. docker stop container   ==============>> stops a container [Replace container with Container ID/name]
21. docker start container   ==============>> starts a container
22. docker restart container   ==============>> restarts the container
23. docker pause container   ==============>> pauses the container [Status:paused]
24. docker unpause container   ==============>> unpauses the container
25. docker inspect container   ==============>> shares the container information in JSON format
26. docker stats container   ==============>> current CPU/memory stats of a container
27. docker top container   ==============>> current load, resource usage on a container
28. docker rm -f container   ==============>> forcefully removes a container completely
29. docker kill container   ==============>> kills the container process, the container remains in the Exit state
30. docker rename old_name new_name   ==============>> renames the container
31. docker tag oldimage:tag newimage:tag   ==============>> used for image tagging
32. docker history image   ==============>> shows the history of an image
33. docker exec -it container /bin/bash   ==============>> accesses the container via SSH
34. docker logs -f container   ==============>> shares the real-time logs of a container
35. docker export container > image.tar   ==============>> exports the container into an image tar
36. docker import image.tar newimage:latest   ==============>> imports the .tar into an image
37. docker login   ==============>> login to your image repository
38. docker push  image:tag  ==============>> pushes the image into the repository
39. docker logout   ==============>> log out of your repo
40. docker cp package.json container:/opt   ==============>> copies a file into a container
41. docker network ls   ==============>> lists down the current docker networks
42. docker network create mynetwork   ==============>> create a new docker network
43. docker run -it -d --network mynetwork ubuntu /bin/bash   ==============>> run the container with your own network
44. docker network connect mynetwork container   ==============>> connect a container with a network
45. docker network disconnect mynetwork container   ==============>> disconnect a container from a network
46. docker network rm mynetwork   ==============>> deletes the docker network
47. docker volume ls     ==============>> shows the current volumes
48. docker volume create myvolume    ==============>> creates a new volume
49. docker run -it -d -v myvolume:/mydata ubuntu /bin/bash    ==============>> mount a volume to your container
50. docker rm -f $(docker ps -a -q)   ==============>> removes/deletes all running/paused/exit containers
51. docker rmi -f $(docker images -a -q)   ==============>> removes all docker images
52. docker system prune   ==============>> removes everything on one go like images, volumes, networks, containers [Dangerous command]
