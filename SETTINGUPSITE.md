1. pull the code https://github.com/suresh-kumara-gist/lando-opensocial-democontent to your webroot directory 

/var/www/html/lando-opensocial-democontent 

2. $ cd /var/www/html/lando-opensocial-democontent

3. import database drupal9.2022-11-27-1669539774.sql.gz into your mysql database and delete or move drupal9.2022-11-27-1669539774.sql.gz  file some other directory.

4. edit settings.php file cd /var/www/html/lando-opensocial-democontent/html/sites/default/settings.php

 I. change database details to your database:

    $databases['default']['default'] = array (
    'database' => 'drupal9',
    'username' => 'drupal9',
    'password' => 'drupal9',
    'prefix' => '',
    'host' => 'database',
    'port' => '3306',
    'namespace' => 'Drupal\\Core\\Database\\Driver\\mysql',
    'driver' => 'mysql',
    );

II. set private directory 

    $settings['file_private_path'] = '';


5. ensure that all the files and folder permissions are set properly.


6. solr setup for indexing in solr (optional but it is required if you have more contents)

7. point your  virtual hosts for Drupal sites and subsites to 
/var/www/html/lando-opensocial-democontent/html

Site works fine with php 7.4 and php 8.0