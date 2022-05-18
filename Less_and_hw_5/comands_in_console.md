home-rim@homerim-desktop:~$ pwd
    /home/home-rim
home-rim@homerim-desktop:~$ ls
home-rim@homerim-desktop:~$ cd L5\ 2/
home-rim@homerim-desktop:~/L5 2$ ls
    L5  __MACOSX
home-rim@homerim-desktop:~/L5 2$ cd L5/
home-rim@homerim-desktop:~/L5 2/L5$ ls
    etl_1.ipynb  L5_pg_source  L5_pg_target  resultsfile.csv  tcph
home-rim@homerim-desktop:~/L5 2/L5$ cd L5_pg_source/
home-rim@homerim-desktop:~/L5 2/L5/L5_pg_source$ ls
    docker-compose.yml
home-rim@homerim-desktop:~/L5 2/L5/L5_pg_source$ docker-compose up -d
    Command 'docker-compose' not found, but can be installed with:
    sudo snap install docker          # version 20.10.12, or
    sudo apt  install docker-compose  # version 1.25.0-1
    See 'snap info docker' for additional versions.
home-rim@homerim-desktop:~/L5 2/L5/L5_pg_source$ sudo snap install docker
home-rim@homerim-desktop:~/L5 2/L5/L5_pg_source$ docker-compose --version
home-rim@homerim-desktop:~/L5 2/L5/L5_pg_source$ docker-compose up -d
    Traceback (most recent call last):
        File "/snap/docker/1779/lib/python3.6/site-packages/urllib3/connectionpool.py", line 710, in urlopen
 
home-rim@homerim-desktop:~/L5 2/L5/L5_pg_source$ sudo apt  install docker-compose
home-rim@homerim-desktop:~/L5 2/L5/L5_pg_source$ docker-compose up -d
    Traceback (most recent call last):
    File "/snap/docker/1779/lib/python3.6/site-packages/urllib3/connectionpool.py", line 710, in urlopen
home-rim@homerim-desktop:~/L5 2/L5/L5_pg_source$ docker -v
    Docker version 20.10.16, build aa7e414
home-rim@homerim-desktop:~/L5 2/L5/L5_pg_source$ docker-compose version
    docker-compose version 1.29.2, build unknown
    docker-py version: 5.0.3
    CPython version: 3.6.9
    OpenSSL version: OpenSSL 1.1.1  11 Sep 2018
home-rim@homerim-desktop:~/L5 2/L5/L5_pg_source$ pip install docker-compose
    Requirement already satisfied: docker-compose in /usr/lib/python3/dist-packages (1.25.0)
home-rim@homerim-desktop:~/L5 2/L5/L5_pg_source$ docker-compose up -d
    Traceback (most recent call last):
    File "/snap/docker/1779/lib/python3.6/site-packages/urllib3/connectionpool.py", line 710, in urlopen

home-rim@homerim-desktop:~/L5 2/L5/L5_pg_source$ docker -v
    Docker version 20.10.16, build aa7e414
home-rim@homerim-desktop:~/L5 2/L5/L5_pg_source$ docker-compose version
    docker-compose version 1.29.2, build unknown
    docker-py version: 5.0.3
    CPython version: 3.6.9
    OpenSSL version: OpenSSL 1.1.1  11 Sep 2018


home-rim@homerim-desktop:~/L5 2/L5/L5_pg_source$ sudo systemctl start docker
home-rim@homerim-desktop:~/L5 2/L5/L5_pg_source$ sudo docker ps
    CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
home-rim@homerim-desktop:~/L5 2/L5/L5_pg_source$ sudo docker-compose up -d
    Creating network "l5_pg_source_default" with the default driver
    Creating volume "l5_pg_source_my_dbdata" with default driver
home-rim@homerim-desktop:~/L5 2/L5/L5_pg_source$ sudo docker ps
    CONTAINER ID   IMAGE         COMMAND                  CREATED          STATUS         PORTS         NAMES
home-rim@homerim-desktop:~/L5 2/L5/L5_pg_source$ cd ..
home-rim@homerim-desktop:~/L5 2/L5$ ls
    etl_1.ipynb  L5_pg_source  L5_pg_target  resultsfile.csv  tcph
home-rim@homerim-desktop:~/L5 2/L5$ cd L5_pg_target/
home-rim@homerim-desktop:~/L5 2/L5/L5_pg_target$ sudo docker-compose up -d
    Creating network "l5_pg_target_default" with the default driver
    Creating volume "l5_pg_target_my_dbdata" with default driver


home-rim@homerim-desktop:~/L5 2/L5/L5_pg_target$ sudo docker ps
    CONTAINER ID   IMAGE         COMMAND                  CREATED         STATUS         PORTS        NAMES

home-rim@homerim-desktop:~/L5 2/L5/L5_pg_target$ sudo docker exec -it my_postgres psql -U root -c "create database my_database"
    CREATE DATABASE
home-rim@homerim-desktop:~/L5 2/L5/L5_pg_target$ sudo docker exec -it my_postgres2 psql -U root -c "create database my_database"
    CREATE DATABASE
home-rim@homerim-desktop:~/L5 2/L5/L5_pg_target$ cd ..
home-rim@homerim-desktop:~/L5 2/L5$ ls
    etl_1.ipynb  L5_pg_source  L5_pg_target  resultsfile.csv  tcph
home-rim@homerim-desktop:~/L5 2/L5$ cd tcph/

home-rim@homerim-desktop:~/L5 2/L5/tcph$ ls
    customer.tbl  dss.ddl  lineitem.tbl  nation.tbl  orders.tbl  partsupp.tbl  part.tbl  region.tbl  supplier.tbl

home-rim@homerim-desktop:~/L5 2/L5/tcph$ sudo docker cp ./dss.ddl my_postgres:/
home-rim@homerim-desktop:~/L5 2/L5/tcph$ sudo docker cp ./customer.tbl my_postgres:/
home-rim@homerim-desktop:~/L5 2/L5/tcph$ sudo docker cp ./lineitem.tbl my_postgres:/
home-rim@homerim-desktop:~/L5 2/L5/tcph$ sudo docker cp ./nation.tbl my_postgres:/
home-rim@homerim-desktop:~/L5 2/L5/tcph$ sudo docker cp ./orders.tbl my_postgres:/
home-rim@homerim-desktop:~/L5 2/L5/tcph$ sudo docker cp ./part.tbl my_postgres:/
home-rim@homerim-desktop:~/L5 2/L5/tcph$ sudo docker cp ./partsupp.tbl my_postgres:/
home-rim@homerim-desktop:~/L5 2/L5/tcph$ sudo docker cp ./region.tbl my_postgres:/
home-rim@homerim-desktop:~/L5 2/L5/tcph$ sudo docker cp ./supplier.tbl my_postgres:/
home-rim@homerim-desktop:~/L5 2/L5/tcph$ sudo docker exec -it my_postgres psql my_database -f dss.ddl
sudo docker exec -it my_postgres psql my_database -c "\copy customer FROM '/customer.tbl' CSV DELIMITER '|'"
sudo docker exec -it my_postgres psql my_database -c "\copy lineitem FROM '/lineitem.tbl' CSV DELIMITER '|'"
sudo docker exec -it my_postgres psql my_database -c "\copy nation FROM '/nation.tbl' CSV DELIMITER '|'"
sudo docker exec -it my_postgres psql my_database -c "\copy orders FROM '/orders.tbl' CSV DELIMITER '|'"
sudo docker exec -it my_postgres psql my_database -c "\copy part FROM '/part.tbl' CSV DELIMITER '|'"
sudo docker exec -it my_postgres psql my_database -c "\copy partsupp FROM '/partsupp.tbl' CSV DELIMITER '|'"
sudo docker exec -it my_postgres psql my_database -c "\copy region FROM '/region.tbl' CSV DELIMITER '|'"
sudo docker exec -it my_postgres psql my_database -c "\copy supplier FROM '/supplier.tbl' CSV DELIMITER '|'"CREATE TABLE
    CREATE TABLE
    CREATE TABLE
    CREATE TABLE
    CREATE TABLE
    CREATE TABLE
    CREATE TABLE
    CREATE TABLE

home-rim@homerim-desktop:~/L5 2/L5/tcph$ sudo apt-get install libpq-dev python-dev
home-rim@homerim-desktop:~/L5 2/L5/tcph$ sudo pip install psycopg2

home-rim@homerim-desktop:~/L5 2/L5/tcph$ sudo docker exec -it my_postgres psql          my_database -c "\copy customer FROM '/customer.tbl' CSV DELIMITER '|'"
    COPY 150000

home-rim@homerim-desktop:~/L5 2/L5/tcph$ sudo pip install pandas

home-rim@homerim-desktop:~/L5 2/L5/tcph$ sudo docker exec -it my_postgres psql my_database -c "\copy lineitem FROM '/lineitem.tbl' CSV DELIMITER '|'"
    COPY 6001215
home-rim@homerim-desktop:~/L5 2/L5/tcph$ sudo docker exec -it my_postgres psql my_database -c "\copyorders FROM '/orders.tbl' CSV DELIMITER '|'"
    COPY 1500000
home-rim@homerim-desktop:~/L5 2/L5/tcph$ sudo docker exec -it my_postgres psql my_database -c "\copypart FROM '/part.tbl' CSV DELIMITER '|'"
    COPY 200000
home-rim@homerim-desktop:~/L5 2/L5/tcph$ sudo docker exec -it my_postgres psql my_database -c "\copypartsupp FROM '/partsupp.tbl' CSV DELIMITER '|'"
    COPY 800000
home-rim@homerim-desktop:~/L5 2/L5/tcph$ sudo docker exec -it my_postgres psql my_database -c "\copyregion FROM '/region.tbl' CSV DELIMITER '|'"
    COPY 5
home-rim@homerim-desktop:~/L5 2/L5/tcph$ sudo docker exec -it my_postgres psql my_database -c "\copysupplier FROM '/supplier.tbl' CSV DELIMITER '|'"
    COPY 10000