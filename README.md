# mysql2kibana

A simple tool used to load a mysql database table into elasticsearch index and after manage it from kibana.
# Configuration
1 Setup the dababase connection, on the docker-compose.yml, under service: logstash
1.2 Database host: 
    extra_hosts:
       db: x.x.x.x
       
1.3 Mysql login: 
    
    - DB_PORT=3306
    - DB_DATABASE=database_name
    - DB_USERNAME=database_username
    - DB_PASSWORD=database_password
    
1.4
