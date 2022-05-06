exercicio de docker com 2 container
1 - mysql 5.7 
2 - flask web

  docker pull mysql:5.7

  docker run --name mysql5 -e MYSQL_ROOT_PASSWORD=mudar123 -p 3307:3307 -d mysql:5.7

  docker ps

  docker network inspect bridge

## colocar o parametro host de acordo com o resultado do comando acima
  mysql -uroot -p --host=172.17.0.*

  pip install flask-mysql

 docker image build -t python-web .

 docker run -p 5050:5050 -d python-web

DOCKER COMPOSE

  docker-compose up

  docker network inspect bridge

  docker-compose ps

  ## conforme id do container retornado do comando acima
  docker exec -it e9ce83871c83 /bin/bash

  create schema teste;

  use teste;
  
CREATE TABLE tbl_user ( user_id BIGINT NOT NULL AUTO_INCREMENT, user_name VARCHAR(45) NULL, categoria VARCHAR(45) NULL, preco int NULL, PRIMARY KEY (user_id));
  

DELIMITER //
CREATE PROCEDURE `sp_createUser`(   IN p_name VARCHAR(20),
    IN p_categoria VARCHAR(20),    IN p_preco VARCHAR(20))
BEGIN
    IF ( select exists (select 1 from tbl_user where user_username = p_username) ) THEN     
        select 'Username Exists !!';     
    ELSE     
        insert into tbl_user
        (
            user_name,
            categoria,
            preco
        )
        values
        (
            p_name,
            p_categoria,
            p_preco
        );     
    END IF;
END //
DELIMITER ;



