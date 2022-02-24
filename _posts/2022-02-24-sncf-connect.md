---
layout: post
title:  "SNCF Error"
date:   2022-02-24
categories: blog, sncf
---

I tried to buy a ticket on <sncf-connect.com> and was presented with the following error:

![Error Message](/assets/error-message.png)

"No retrieval options available for this journey. Seats on this train cannot be reserved. Select another journey."

Which doesn't really tell you anything. A bit more searching

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

turns up this page: <https://www.sncf-connect.com/en-be/help/eticket-not-offered>

which is a bit more helpful:

> if you have a few different journey legs included in your booking, it could be
> that the various ticket collection types might not be compatible with each
> other. in this case, we can offer you home delivery, which is the most common
> collection method for all carriers. depending on the date of your journey,
> however, sometimes the time frame for receiving your tickets may be too short,
> meaning it’s impossible to reserve your trip.<br><br>
>
> don't panic! here are some tips ;)<br><br>
>
> you just need to make a separate booking for each section of your journey, and
> if the journey is eligible for an e-ticket, this option will be offered.
