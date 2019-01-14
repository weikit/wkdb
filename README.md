# wkdb
PDO mysql support for Wordpress
* Tags: database, backend, pdo, mysql
* Tested up to: 5.0.0
* License: GPLv2 or later


## Install

1. copy `db.php` file to `your_wordpress_project/wp-contents`.

## Usage

```php
// Compatible with $wpdb methods
$wpdb->prepare( "SELECT * FROM `table` WHERE `column` = %s AND `field` = %d OR `other_field` LIKE %s", array( 'foo', 1337, '%bar' ) );
$wpdb->prepare( "SELECT DATE_FORMAT(`field`, '%%c') FROM `table` WHERE `column` = %s", 'foo' );
...

// convert pdo named or unnamed placeholder to wpdp placeholders style
$result = convert_pdo_placeholders("SELECT * FROM wp_users where user_login=:user_login", array(':user_login' => 'admin'));
// $result = convert_pdo_placeholders("SELECT * FROM wp_users where user_login=?", array('admin'));
$sql = call_user_func_array(array($wpdb, 'prepare'), $result);
```
