* goal
  * configure Docker

# Alpine image
* `docker run -d --name=grafana -p 3000:3000 grafana/grafana:main`
* clean ALL
  * `docker kill grafana`
  * `docker container prune`

# Ubuntu image
* `docker run -d --name=grafana -p 3000:3000 grafana/grafana:main-ubuntu`
* clean ALL
  * `docker kill grafana`
  * `docker container prune`

## Enterprise
* `docker run -d --name=grafana -p 3000:3000 grafana/grafana-enterprise:main-ubuntu`
* clean ALL
  * `docker kill grafana`
  * `docker container prune`

## Open Source
* `docker run -d --name=grafana -p 3000:3000 grafana/grafana-oss:main-ubuntu`
* clean ALL
  * `docker kill grafana`
  * `docker container prune`

# specific Grafana version
* _Example:_
  * `docker run -d -p 3000:3000 --name grafana grafana/grafana-enterprise:9.4.7`

# default paths
* `docker inspect grafana | grep -A 20 "Env"`

# 
