
install apache2
install mysql-client
toot


add-apt-repository -y ppa:ondrej/php
apt install php5.6 php5.6-mysqli -y
cp index.php to /var/www/html/
create rds db

take rds endpoint and confiure details in index.php
create table in data in my sql db.
insert records.

create ami of the ec2
create LC
creats ASG
create new lbroute 53
insert records
do failover


https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/multi-az-db-clusters-concepts.html#multi-az-db-clusters-concepts-failover
