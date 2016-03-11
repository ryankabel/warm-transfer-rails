# Warm Transfer: Transfer support calls from one agent to another using ruby on rails
[![Build Status](https://travis-ci.org/TwilioDevEd/warm-transfer-rails.svg)](https://travis-ci.org/TwilioDevEd/warm-transfer-rails)

## Local development

This project is built using the [Ruby on Rails](http://rubyonrails.org/) web framework.

1. First clone this repository and `cd` into it:
   ```bash
   $ git clone git@github.com:TwilioDevEd/warm-transfer-rails.git
   $ cd warm-transfer-rails
   ```

1. Install the dependencies:
   ```bash
   $ bundle
   ```

1. Copy the sample configuration file and edit it to match your configuration

  ```bash
  $ cp .env.example .env
  ```

 You can find your `TWILIO_ACCOUNT_SID` and `TWILIO_AUTH_TOKEN` in your
 [Twilio Account Settings](https://www.twilio.com/user/account/settings).
 You will also need a `TWILIO_NUMBER`, which you may find [here](https://www.twilio.com/user/account/phone-numbers/incoming).

 Run `source .env` to export the environment variables

1. Create database and run migrations:

   _Make sure you have installed [PostgreSQL](http://www.postgresql.org/). If on
   a Mac, I recommend [Postgres.app](http://postgresapp.com)_.

   ```bash
   $ bundle exec rake db:setup
   ```

1. Make sure the tests succeed:
   ```bash
   $ bundle exec rspec
   ```

1. Run the server:
   ```bash
   $ bundle exec rails s
   ```

1. Expose your application to the wider internet using [ngrok](http://ngrok.com). You can click
  [here](#expose-the-application-to-the-wider-internet) for more details. This step
  is important because the application won't work as expected if you run it through
  localhost.

  ```bash
  $ ngrok http 3000
  ```

  Once ngrok is running, open up your browser and go to your ngrok URL. It will
  look something like this: `http://9a159ccf.ngrok.io`

1. Configure Twilio to call your webhooks

  You will also need to configure Twilio to call your application when calls are received on your `TWILIO_NUMBER`. The voice url should look something like this:

  ```
  http://9a159ccf.ngrok.io/conference/connect/client
  ```
  
  ![Configure Voice](http://howtodocs.s3.amazonaws.com/twilio-number-config-all-med.gif)


That's it!

### Expose the Application to the Wider Internet

If you want your application to be accessible from the internet, you can either
forward the necessary ports in your router, or use a tool like
[ngrok](https://ngrok.com/) that will expose your local host to the internet.

You can read [this blog post](https://www.twilio.com/blog/2015/09/6-awesome-reasons-to-use-ngrok-when-testing-webhooks.html)
for more details on how to use ngrok, but if you are using version 2.x, exposing
a specific port should be easily done with the following command:

```bash
$ ngrok http 3000
```

## Meta

* No warranty expressed or implied. Software is as is. Diggity.
* [MIT License](http://www.opensource.org/licenses/mit-license.html)
* Lovingly crafted by Twilio Developer Education.
