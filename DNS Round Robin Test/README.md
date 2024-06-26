# DNS Round Robin Test

- Ever since Docker Engine 1.11, we can have multiple containers on a created network respond to the same DNS address
- Create a new virtual network (default bridge driver) 
- Create two containers from elasticsearch:2 image
- Research and use --network-alias when creating them to give them an additional DNS name to respond to
- Run alpine nslookup search with --net to see the two containers list for the same DNS name
- Run centos curl -s search:9200 with --net multiple times until you see both "name" fields show

# CODE

```bash
docker network create dude
docker container run -d --net dude --net-alias search elasticsearch:2
docker container run -d --net dude --net-alias search elasticsearch:2
docker container run --rm --net-dude alias nslookup search
docker container run --rm --net-dude centos curl -s search:9200
```