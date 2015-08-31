PHP Library For Twilio Wrapper
=========================

Class
-----

There's one primary class named `TwilioWrapper` that wraps all major functions.

Initialization
--------------

```php
$wrapperObj = new TwilioWrapper($to_number, $twilio_details, $callback_details);
```

Configuration Parameters
------------------------

- ####$to_number:  *e.g. '+1234567890'*
	> This is the number the customer will provide to us, and we will call back to this number as soon as user submits a call request.

- ####$twilio_details:  *array($account_credentials, $twilio_phone_number)*
	- #####$account_credentials:  *array($sid, $token)*
		> - **$sid:** Twilio account sid. *(you can get it from Twilio account dashboard)*

		> - **$token:** Twilio account token *(you can get it from Twilio account dashboard)*  

	- #####$phone_number

		>Twilio phone number that is assigned to given Twilio account by Twilio system and it will be used as `from` number to call the customer phone.

	- #####$callback_details

		This includes the details of our actual thinQ line that will be linked to customer once he accepts our followup call.

		- **$type:** Type of support line - can be either `sip` for custom voip, or `phone` for normal phone number.

		- **$detail:** Array of details according to `$type`.  

			if `$type` is `sip`, details are like this:

			- **$id:** `id` part of the SIP URI. 

				*e.g. 'Jack'*

			- **$domain:** `domain` part of the SIP URI. 

				*e.g. 'example.com'*

			- **$headers:** `headers` that is appended to the end of the SIP URI.

				e.g. 

					array( 
						'thinQid' => '11001', 
						'thinQtoken' => '0c82a54f22f775a3ed8b97b2dea74036' 
					)

			if `$type` is `phone`, details only include the target number:

			- **$id:** the target thinQ line's `phone number`

Initiate a call to the thinQ line
------------------------------------

```php
	$result = $obj->call()
```

> **Return Value**: Proper Twilio Call object if `success`, or relevant error message otherwise

Quick Start Guide
-----------------

```
<?

require_once("lib/twilio-wrapper/class.php");

$customer_phone_no = $_REQUEST['customer_phone_no'];

if(!empty($customer_phone_no)){
    $obj = new TwilioWrapper(
        $customer_phone_no,                           // Customer phone number
        //'+1234567890',
        array(                                          // Your Twilio credentails
            'twilio_account' => array( 'sid' => 'ACa5a21802beff96f147d40bf98c957038', 'token' => '7852c807435af28d468344ca57a49d2a'),
            'twilio_number' => '+1234567890'
        ),                                              // Your thinQ endpoint
        array(
            'type' => 'sip',                          // can be 'sip' or 'phone'
            'detail' => array(                                      // SIP details here
                'id' => '19196356566',
                'domain' => 'wap.thinq.com',
                'headers' => array(
                    'thinQid' => '11001',
                    'thinQtoken' => '0c82a54f22f775a3ed8b97b2dea74036'
                )
            )  //or
            /*'type' => 'phone',
            'detail' => array(
                'id' => '+1234567890'                // twilio number or valid phone number
            )*/

        )
    );
    if($result = $obj->call()) {
        $message = "A call will be made shortly to your number!";
    }else{
        $message= "Call failed due to some errors.";
    }
}

?>

<html>
<heaD>
    <title>Twilio Custom Library Wrapper Demo</title>
</heaD>
<body>
    <div class="message"><?= $message ?></div>
    <br/><br/>
    <form name="customer_form" action="" method="post">
        <label for="customer_phone_no">Your Phone Number: </label>
        <input type="text" name="customer_phone_no" />
        <input type="submit" value="Call thinQ line" />
    </form>
    <br/><br/>
    <? if(isset($result) && $result){ ?>
        <div>
            <h1>Call Details:</h1>
            <p><pre><?= print_r($result) ?></pre></p>
        </div>
    <? } ?>
</body>
</html>
```