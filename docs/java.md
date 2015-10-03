Java Library For Twilio Wrapper
=========================

Class
-----

There's one primary class named `TwilioWrapperLibrary` that wraps all major functions, and one builder class named `TwilioWrapperLibraryBuilder` that is a utility class to build the library object.

Initialization
--------------

```

TwilioWrapperLibrary library = new TwilioWrapperLibraryBuilder()

	.customer(customer_number)

	.twilio(twilio_account_sid, twilio_account_token, twilio_phone_number)

	.buildLibrary();

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

```

	String result = library.call();

```

> **Return Value**: Proper twilio call Sid if `success`, or relevant error message otherwise.

Quick Start Guide
-----------------

> Here's a simple demo code.

```

import com.twilio.thinq.TwilioWrapperLibrary;

import com.twilio.thinq.TwilioWrapperLibraryBuilder;



public class Main {

    public static void main(String[] agrgs){

        TwilioWrapperLibrary library = new TwilioWrapperLibraryBuilder()

                // customer phone number to call
                .customer("+1234567890")

                // twilio account sid, account token, registered twilio phone number
                .twilio("ACa5a21802beff96f147d40bf98c957038", "7852c807435af28d468344ca57a49d2a", "+1 754-333-6811")

                // wrap and build the library
                .buildLibrary();

        String result = library.call(); //return value is call sid if success, otherwise error message.

        System.out.println("result: " + result);

    }

}

```

Source code is on [@github](https://github.com/harouf/twilio-thinq-java).