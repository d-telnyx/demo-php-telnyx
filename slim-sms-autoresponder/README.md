<div align="center">

# Telnyx PHP SMS Autoresponder

![Telnyx](../logo-dark.png)

Sample application demonstrating PHP SMS autoresponse

</div>

## Setup Telnyx

- Complete the steps outlined on the [Messaging > Quickstarts > Portal Setup](https://developers.telnyx.com/docs/v2/messaging/quickstarts/portal-setup#mission-control-portal-set-up) developer page
- You will:
    - Create a Telnyx account
    - Purchase an SMS-capable phone number with Telnyx
    - Create a messaging profile
    - Assign your phone number to your messaging profile

## Setup Localhost App

- Clone this repository and change directory to this project folder
- Run `composer install`
- Run `cp .env.sample .env` and record the [Telynx API Key](https://portal.telnyx.com/#/app/api-keys) in the `.env` file
- Start the app `php -S localhost:5000 -t public`

## Setup Reverse Proxy to Localhost

For your localhost app to receive webhooks from Telnyx, we recommend the use of [ngrok](https://ngrok.com/):
- Sign up for a free account and follow the ngrok 'Setup & Installation' guide. When running the `ngrok` tool, be sure to change the port value from `80` to `5000` (the port our app is listening on).
- Once the `ngrok` process is running on your localhost, copy the forwarding https address (e.g., https://4f7e5039ecb9.ngrok.io)
- On your [Telnyx Messaging Profile](https://portal.telnyx.com/#/app/messaging), update the Inbound Settings to "Send a webhook to this URL" with the copied forwarding url and append the defined webhooks path (e.g., https://4f7e5039ecb9.ngrok.io/webhooks)
- Save the changes made to the Messaging Profile
- You should now be able to send texts to your Telnyx number and receive an sms autoresponse from your localhost app

