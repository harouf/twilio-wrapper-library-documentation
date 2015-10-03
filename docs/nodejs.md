NodeJS Library For Twilio Wrapper
=========================

Class
-----

There's one primary class named `TwilioWrapper` that wraps all major functions as prototype methods.

Initialization
--------------

```javascript

var wrapper = new TwilioWrapper(

        customer_number,                             	// Customer phone number

        twilio_accountSid,           					// twilio account sid  

        twilio_authToken,            					// twilio account token

        twilio_phone_number                             // twilio phone number

    );

```

Configuration Parameters
------------------------

- ####customer_number:  *e.g. '+1234567890'*
	> This is the number the customer will provide to us, and we will call back to this number as soon as user submits a call request.

- ####twilio_account_sid:
	
	> You can get Twilio account sid from your Twilio account dashboard.

- ####twilio_account_token:

	> You can get Twilio account token from your Twilio account dashboard.

- ####twilio_phone_number:

	>Twilio phone number that is assigned to given Twilio account by Twilio system and it will be used as `from` number to call the customer phone.

Initiate a call to the thinQ line
------------------------------------

```javascript

	var return_promise = wrapper.call();

```

> **Return Value**: Proper promise object for the initiated twilio call if `success`, or `null` otherwise.

Quick Start Guide
-----------------

> Here's a simple demo code.

```javascript

var TwilioWrapper = require('twilio-thinq-node');


var customer_number = '+1234567890';

var twilio_accountSid = 'ACa5a21802beff96f147d40bf98c957038';

var twilio_authToken = '7852c807435af28d468344ca57a49d2a';

var twilio_phone_number = '+1 754-333-6811';


var wrapper = new TwilioWrapper(

        customer_number,                             	// Customer phone number

        twilio_accountSid,           					// twilio account sid  

        twilio_authToken,            					// twilio account token

        twilio_phone_number                             // twilio phone number

    );


var return_promise = wrapper.call();


return_promise.then(function(call){

	console.log("Successfully initiated a new call to customer!");

	console.log("Call sid: " + call.sid);

}, function(error){

	console.log(err);

});


```

Source code is on [@github](https://github.com/harouf/twilio-thinq-node).