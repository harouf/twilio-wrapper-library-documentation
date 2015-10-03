Ruby Library For Twilio Wrapper
=========================

Class
-----

There's one primary class named `TwilioWithThinq::TwilioWrapper` that wraps all major functions.

Initialization
--------------

```ruby

wrapper = TwilioWithThinq::TwilioWrapper.new customer_number, twilio_account_sid, twilio_account_token, twilio_phone_number

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

```ruby

	call_sid = wrapper.call

```

> **Return Value**: Proper twilio call Sid if `success`, or relevant error message otherwise.

Quick Start Guide
-----------------

> Here's a simple demo code.

```ruby

require "twilio_with_thinq"


customer_number = "+1234567890"

twilio_account_sid = "ACa5a21802beff96f147d40bf98c957038"

twilio_account_token = "7852c807435af28d468344ca57a49d2a"

twilio_phone_number = "+17543336811"



wrapper = TwilioWithThinq::TwilioWrapper.new customer_number, twilio_account_sid, twilio_account_token, twilio_phone_number


call_sid = wrapper.call


puts "Call sid: #{call_sid}"

```

Source code is on [@github](https://github.com/harouf/twilio-thinq-ruby).