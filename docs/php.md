PHP Library
===========

Class
-----

There's one primary class named `TwilioWrapper` that wraps all major functions.

Initialization
--------------

```php

$wrapperObj = new TwilioWrapper($customer_number, $twilio_account_sid, $twilio_account_token, $twilio_phone_number);

```

Configuration Parameters
------------------------

- ####$customer_number:  *e.g. '+1234567890'*
	> This is the number the customer will provide to us, and we will call back to this number as soon as user submits a call request.

- ####$twilio_account_sid:
	
	> You can get Twilio account sid from your Twilio account dashboard.

- ####$twilio_account_token:

	> You can get Twilio account token from your Twilio account dashboard.

- ####$twilio_phone_number:

	>Twilio phone number that is assigned to given Twilio account by Twilio system and it will be used as `from` number to call the customer phone.

Initiate a call to the thinQ line
------------------------------------

```php

	$result = $obj->call();

```

> **Return Value**: Proper twilio call Sid if `success`, or relevant error message otherwise.

Quick Start Guide
-----------------

> Here's a simple demo code.

```

<?php

require_once __DIR__ . '/vendor/autoload.php'; 

use TwilioWithThinq\TwilioWrapper;

$customer_phone_no = $_REQUEST['customer_phone_no'];

if(!empty($customer_phone_no)){

    $obj = new TwilioWrapper(

        $customer_phone_no,   // Customer phone number
        //'+1234567890',

        'ACa5a21802beff96f147d40bf98c957038',          // twilio account sid  

        '7852c807435af28d468344ca57a49d2a',            // twilio account token

        '+1 754-333-6811'                               // twilio phone number

    );

    echo "Call sid: ". $obj->call(). PHP_EOL;

}

?>

<html>

<head>

    <title>Twilio Custom Library Wrapper Demo</title>

</head>

<body>

    <div class="message"><?= $message ?></div>

    <br/><br/>

    <form name="customer_form" action="" method="post">

        <label for="customer_phone_no">Your Phone Number: </label>

        <input type="text" name="customer_phone_no" />

        <input type="submit" value="Call thinQ line" />

    </form>

    <br/><br/>

</body>

</html>

```

Source code is on [@github](https://github.com/harouf/twilio-thinq-php).