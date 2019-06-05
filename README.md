# mysql2kibana

A simple tool used to load a mysql database table into elasticsearch index and after manage it from kibana.

# Configuration
1 Setup the dababase connection, on the docker-compose.yml, under service: logstash

1.2 Database host, on the docker-compose service logstash, expose the database host internally: 

    extra_hosts:
       db: x.x.x.x
       
1.3 Mysql login: 
    
    - DB_PORT=3306
    - DB_DATABASE=database_name
    - DB_USERNAME=database_username
    - DB_PASSWORD=database_password
    
1.4 Configure the memory RAM usage for elasticsearch, on the service es01

    - "ES_JAVA_OPTS=-Xms1024m -Xmx1024m"
    
1.5 Configure kibana host URL:
    
    - SERVER_NAME='localhost'
    
    
# Run kibana:
Run docker-compose up -d,  kibana is configured to run under: http://localhost:5601/




