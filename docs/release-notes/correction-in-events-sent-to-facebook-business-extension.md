---
title: "Correction in events sent to Facebook Business Extension"
slug: "correction-in-events-sent-to-facebook-business-extension"
createdAt: "2022-11-21T13:55:00.000Z"
hidden: false
---
The [Facebook Business Extension and Conversions API app](https://developers.vtex.com/vtex-developer-docs/docs/vtex-facebook-fbe) is the one-stop shop for merchants to easily connect their stores to Facebook services through the FBE platform. 

Through the app, a series of events are sent from VTEX servers to Facebook to track a store's performance. 

Some customers have reported that the server events below were being sent triplicated to Facebook - except for purchase events.

| Event              		| Server status 	|
|--------------------	|--------------------	|
| Page View          	          | :warning:	|
| Content View                  | :warning: 	|
| Search             	         | :warning: 	|
| Add To Cart        	 | :warning: 	|
| Initiate Checkout    | :warning: 	|
| Purchase           	  | ✅ 	|


:white-check-mark: **We have adjusted our app's architecture to fix this issue, so that events won't be triplicated anymore. **

Due to this correction, users might see an expressive change change in the number of events received, since the numbers of events will decrease from now on. This is the expected behavior.