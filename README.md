# ansible-study
* Repositório dedicado com a finalidade de estudo do Ansible. Proposto como Desafio pelo Diogo Lima
* yum update
* yum install epel-release yum-utils
* yum install http://rpms.remirepo.net/enterprise/remi-release-7.rpm 
* yum update
* yum-config-manager --enable remi-php70
* yum install php php-mysql php-fpm
* systemctl start php-fpm
* systemctl enable php-fpm
* yum install mariadb-server mariadb
* sudo systemctl start mariadb
* sudo systemctl enable mariadb
* mysql -u root -p
* CREATE DATABASE desafio CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci;
* GRANT ALL ON desafio.* TO 'desafio'@'localhost' IDENTIFIED BY 'desafio';
* FLUSH PRIVILEGES;
* quit
* sudo yum install nginx 
* sudo systemctl start nginx
* sudo systemctl enable nginx
* cd /var/www/html/wordpress
* yum install wget
* wget https://wordpress.org/latest.tar.gz
* tar xfvz latest.tar.gz
* chown nginx:nginx wordpress
- arquivo /etc/php-fpm.d/www.conf
	user: nginx
	group: nginx
	listen = /var/run/php-fpm/php-fpm.sock
	listen.owner = nginx
	listen.group = nginx
- arquivo /etc/nginx/nginx.con
	root /usr/share/nginx/html/wordpress;
        index index.php index.html index.html;
	
	location ~ \.php$ {
            try_files $uri =404;
           fastcgi_pass unix:/var/run/php-fpm/php-fpm.sock;
            fastcgi_index index.php;
            fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
            include fastcgi_params;
        }
