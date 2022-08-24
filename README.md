## payment checkout-js 

# ![Issues](https://img.shields.io/github/issues/harmonizerblinks/payment-checkout-js) ![Star](https://img.shields.io/github/stars/harmonizerblinks/payment-checkout-js) ![Issues](https://img.shields.io/github/license/harmonizerblinks/payment-checkout-js)

Nodejs API for that fixed any Checkout Process.

# [![NPM](https://nodei.co/npm/payment-checkout-js.png)](https://nodei.co/npm/payment-checkout-js/)

### Installation

```
npm install payment-checkout-js
```

### Usaged

```js

var url = "endpoint";

// Require the library
var payment = require('payment-checkout-js')(process.env.APP_ID, process.env.APP_KEY, url);


```

#### Making calls to the resources
The resource methods accepts are promisified, but can receive optional callback as the last argument.

```js
// payment.{resource}
payment.checkout.createPayment({})
	.then((body)=> {
  		console.log(body);
	})
	.catch((error)=> {
		console.log(error);
	});
```



For all resource methods, the JSON body can be passed as the argument.

### Resources

- checkout
  - createPayment
  - getCheckout
  - sendOtp
  - verifyOtp
  - processMomoCheckout
  - processCardCheckout
  - processUssdCheckout
  - verifyPayment

Method to Initiation a checkout payment.

```js
payment.checkout.createCheckout({
	name: 'Firstname Lastname',
	mobile: '+233540000000',
	mobile_network: 'MTN || AIRTEL || TIGO || VODAFONE',
	email: 'harmony@cross-switch.com',
	currency: 'GHS',
	amount: 0.1,
	order_id: `${Math.ceil(Math.random() * 10e8)}`,
	order_desc: 'Testing',
	account: '',
	customerid: '',
	callback: ''
}).then((body)=> {
	console.log(body);
}).catch((error)=> {
	console.log(error);
});
```

Method to process mobile Money on Checkout.

```js
payment.checkout.ProcessMomoCheckout({
	code: '+233540000000',
	mobile_network: 'MTN || AIRTEL || TIGO || VODAFONE',
	email: 'harmony@icloud.com',
	amount: 1,
}).then((body)=> {
	console.log(body);
}).catch((error)=> {
	console.log(error);
});
```


Method to Get Cashout Balance.

```js
payment.checkout.getCheckout({})
.then((body)=> {
	console.log(body);
}).catch((error)=> {
	console.log(error);
});
```

Method to Verify Transaction status.

```js
payment.checkout.verifyPayment({
	order_id: `${data.transaction_no}`,
}).then((body)=> {
	console.log(body);
}).catch((error)=> {
	console.log(error);
});
```


