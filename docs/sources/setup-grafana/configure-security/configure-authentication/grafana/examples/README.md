* `docker compose up -d`

# Grafana basic authentication, by default enabled
* localhost:3000
  * admin/admin

# disable basic authentication
## disable basic auth 
* hit [sample.http](sample.http)
## NOT affect | web login
* http://localhost:3000/login
  * admin/admin

# Password policy
* localhost:3000
  * admin/admin
  * NOT able to set "admin" password 

# disable login form
* localhost:3000
  * NOT display login form
