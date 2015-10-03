.NET (C#) Library
=================

Class
-----

There's one primary class named `TwilioWrapper` that wraps all major functions.

Initialization
--------------

```

TwilioWrapper wrapper = new TwilioWrapper(customer_number, twilio_account_sid, twilio_account_token, twilio_phone_number);

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

	String call_sid = wrapper.call();

```

> **Return Value**: Proper twilio call Sid if `success`, or relevant error message otherwise.

Quick Start Guide
-----------------

> Here's a simple demo code.

```

using System;

using System.Collections.Generic;

using System.Linq;

using System.Text;

using System.Threading.Tasks;

using TwilioWithThinq;


namespace Demo

{

    class Program

    {

        static void Main(string[] args)

        {

            TwilioWrapper wrapper = new TwilioWrapper("+1234567890", "ACa5a21802beff96f147d40bf98c957038", "7852c807435af28d468344ca57a49d2a", "+1 754-333-6811");

            Console.WriteLine("Call sid: " + wrapper.call());

            Console.ReadLine();

        }

    }

}

```

Source code is on [@github](https://github.com/harouf/twilio-thinq-net).