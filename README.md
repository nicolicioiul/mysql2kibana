# mysql2kibana

A simple tool used to load a mysql database table into elasticsearch index and after manage it from kibana. Used to create some analytics dashboard from existing data.

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
    
1.6 To configure the database table, check the file: ./etc/logstash/config/pipeline/logstash.conf. There is an example for table

        CREATE TABLE `logs` (
             `id` int(11) NOT NULL AUTO_INCREMENT,
             `file_name` varchar(512) COLLATE utf32_bin NOT NULL DEFAULT '',
             `logid` varchar(64) COLLATE utf32_bin NOT NULL,
             `datetime` datetime(6) NOT NULL,
             `timestamp` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
             `parsed_message` varchar(4096) COLLATE utf32_bin NOT NULL,
             `message` varchar(4096) COLLATE utf32_bin NOT NULL DEFAULT '',
             `level` varchar(24) COLLATE utf32_bin NOT NULL DEFAULT '',
             PRIMARY KEY (`id`),
             KEY `level` (`level`)
            ) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=utf32 COLLATE=utf32_bin

The table can be changes and modified.
 
    
# Run kibana:
Run docker-compose up -d,  kibana is configured to run under: http://localhost:5601/




