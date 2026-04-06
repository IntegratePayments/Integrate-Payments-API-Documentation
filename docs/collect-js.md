# Collect.js Integration Guide

Collect.js allows you to build a completely custom checkout experience while keeping sensitive cardholder data off your servers. This reduces your PCI DSS compliance scope significantly.

## 💳 How it Works
1. **Initialize**: Load the Collect.js library with your Tokenization Key.
2. **Secure Fields**: Collect.js creates secure iframes for the Card Number and CVV.
3. **Tokenize**: Upon form submission, Collect.js intercepts the data and returns a `payment_token`.
4. **Process**: Send that token to the Integrate Payments API to complete the charge.

---

## 🚀 Step 1: Include the Script
Add this to your HTML header. Replace `YOUR_PUBLIC_KEY_HERE` with the Tokenization Key from your merchant dashboard.

```html
<script src="https://gateway-url.com/tokenization/collect.js" 
        data-tokenization-key="YOUR_PUBLIC_KEY_HERE">
</script>

  
  
  ## 🛠 Step 2: Create the Payment Form

Collect.js will automatically inject secure iframes into these specific `div` IDs.

```html
<form id="my-payment-form">
    <div id="collectjs-card-number"></div>
    <div id="collectjs-cvv"></div>
    <div id="collectjs-expiration"></div>
    
    <button type="submit" id="submit-btn">Pay Now</button>
</form>
  
## 🔄 Step 3: Handle the Response

Add this JavaScript to your page to capture the secure token. This allows you to send the token to your server for processing.

```javascript
CollectJS.configure({
    'callback': function(response) {
        console.log("Tokenization Successful!");
        console.log("Token ID: " + response.token);
        
        // Next: Send 'response.token' to your server 
        // to process the charge via the Direct Post API.
    }
});
