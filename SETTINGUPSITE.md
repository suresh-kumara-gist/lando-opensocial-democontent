1. pull the code https://github.com/suresh-kumara-gist/lando-opensocial-democontent.git to your webroot directory 

/var/www/html/lando-opensocial-democontent 

2. $ cd /var/www/html/lando-opensocial-democontent and run $ composer install

3. import database drupal9.2022-11-27-1669539774.sql.gz into your mysql database and delete or move drupal9.2022-11-27-1669539774.sql.gz  file into some other directory.

4. edit settings.php file cd /var/www/html/lando-opensocial-democontent/html/sites/default/settings.php

 I. change database details to your database:
```
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
```
II. set private directory 
```
    $settings['file_private_path'] = '';
```
III. Change configuration sync directroy to other directory
```
$settings['config_sync_directory'] = 'sites/default/files/config_dGJdaKP-7r_Udqh1gf7MnxOMD4PTc8LOH1WmUQrHYMm5nyBB0DXSgz_3Feuh1m-sloiue6Cy-g/sync';
```

IV. Set trusted host to your domain name
```
$settings['trusted_host_patterns'] = [
  '^example\.com$',
  '^.+\.example\.com$',
  '^example\.org$',
  '^.+\.example\.org$',
];
```

5. ensure that all the files and folder permissions are set properly.


6. solr setup for indexing in solr (optional but it is required if you have more contents)

7. point your  virtual hosts for Drupal sites and subsites to 
/var/www/html/lando-opensocial-democontent/html

Site works fine with php 7.4 and php 8.0

8. remove .lando.yml file and remove .git directory  and setup your own git repository

```
$config['swiftmailer.transport']['transport'] = ''; // 'smtp', etc
$config['swiftmailer.transport']['smtp_host'] = '';
$config['swiftmailer.transport']['smtp_port'] = 123; // e.g. 465
$config['swiftmailer.transport']['smtp_encryption'] = ''; // 'tls', 'ssl', '0' for no encryption.
$config['swiftmailer.transport']['smtp_credential_provider'] = 'swiftmailer';
$config['swiftmailer.transport']['smtp_credentials']['swiftmailer']['username'] = '';
$config['swiftmailer.transport']['smtp_credentials']['swiftmailer']['password'] = '';
```
