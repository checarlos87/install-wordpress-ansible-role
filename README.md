# Ansible Role for Installing Wordpress
An Ansible role for installing Wordpress in a CentOS 6 machine.

The role downloads the latest version of Wordpress as a tarball, unters it and then installs it at the specified directory. It also sets up the MySQL database and renders the appropriate wp-config (with uniquely generated salts).  The MySQL user password is also generated dynamically and it is not required to be typed into any part of the role.

The MySQL modules \([`mysql_db`](http://docs.ansible.com/ansible/mysql_db_module.html) and [`mysql_user`](http://docs.ansible.com/ansible/mysql_user_module.html)) are used with Ansible's defaults.  If the playbook that will use this role runs into trouble logging into the database, you might have to set the `login_*` options of those modules or use Ansbile's [`become`](http://docs.ansible.com/ansible/become.html) directives.

The role takes the following variables:

* `tmp_dir`: a directory to temporarily hold the Wordpress tarball
* `wp_install_dir`: The directory to install wordpress into (default is /var/www/html). A `wordpress` directory holding the tarball contents will be created in this path.
* `wordpress_db`: The name of the MySQL database wordpress will use.
* `wordpress_user`: The MySQL user Wordpress will log in as.  The user will be created if it does not currently exist.  If it currently exists, its password will changed to what the role generates.

