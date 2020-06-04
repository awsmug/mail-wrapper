# Awesome Mail-Wrapper

![](https://github.com/awsmug/mail-wrapper/workflows/PHPUnit/badge.svg)

Version 1.0.0-beta-1

The mail wrapper allows the sending of mails, independent of the used system. 
In this case, the drivers used for this are responsible for sending with the correct mailing functions.

## Use of the mail wrapper

First the appropriate driver must be selected and initialized.

```php
<?php

use awsm\Mail_Wrapper\Driver\Driver_PHP;

$driver = new Driver_PHP();
```

Next, the driver must be passed to the mail class.

```php
<?php

use awsm\Mail_Wrapper\Driver\Driver_PHP;
use awsm\Mail_Wrapper\Mail;

$driver = new Driver_PHP();
$mail = new Mail( $driver );
```

Then the functions from the mail class can be used.

```php
<?php

use awsm\Mail_Wrapper\Driver\Driver_PHP;
use awsm\Mail_Wrapper\Mail;
use awsm\Mail_Wrapper\Mail_Exception;


$driver = new Driver_PHP();
$mail = new Mail( $driver );

try {
    $mail->add_to_email( 'john.doe@dummy.com' )
         ->set_from_name( 'Developer' )
         ->set_from_email( 'developer@dummy.com' )
         ->set_subject( 'Read my mail!' )
         ->set_content( 'Hello John! Greetings from the developer!' )
         ->send();
} catch ( Mail_Exception $e ) {
    echo $e->getMessage();
}
```

## Drivers

The following drivers are currently included in the mail wrapper.

- Driver_PHP
- Driver_WordPress