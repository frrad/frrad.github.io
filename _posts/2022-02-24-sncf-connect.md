---
layout: post
title:  "SNCF Error"
date:   2022-02-24
categories: blog, sncf
---

![Error Message](/assets/error-message.png)

"No retrieval options available for this journey. Seats on this train cannot be reserved. Select another journey."

```json
{
  "title": "CART_NO_DELIVERY_MODE_AVAILABLE",
  "type": "/booking/no-delivery-mode-available",
  "behaviour": "UNRECOVERABLE",
  "details": "No retrieval options available for this journey. Seats on this train cannot be reserved. Select another journey.",
  "description": {
    "message": "No retrieval options available for this journey. Seats on this train cannot be reserved. Select another journey."
  },
  "cause": {
    "title": "Reservation error",
    "type": "/errors/reservation/reservation-error",
    "status": 400
  }
}
```
https://www.sncf-connect.com/en-be/help/eticket-not-offered

if you have a few different journey legs included in your booking, it could be
that the various ticket collection types might not be compatible with each
other. in this case, we can offer you home delivery, which is the most common
collection method for all carriers. depending on the date of your journey,
however, sometimes the time frame for receiving your tickets may be too short,
meaning it’s impossible to reserve your trip.

don't panic! here are some tips ;)

you just need to make a separate booking for each section of your journey, and
if the journey is eligible for an e-ticket, this option will be offered.
