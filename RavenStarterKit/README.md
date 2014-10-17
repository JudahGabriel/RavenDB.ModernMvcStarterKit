# RavenDB Modern MVC Starter Kit

Need a starting point for an ASP.NET MVC project using Raven as the backing store? Look no further.

This project provides:

 - <strong>A RavenDB-backed identity provider</strong>, updated to work with the latest MS Identity Framework (2.1 at the time of this writing).
 - <strong>A registration confirmation system</strong>: when a user registers, he is required to confirm his registration via email. The email is sent via your developer SendGrid account. Upon registering, the user is presented with the following screen:
<img src="http://i.imgur.com/67raMqS.png" />
   The user will receive an email with a confirmation link. Following the link, he'll be taken to this page:
<img src="http://i.imgur.com/FNbzWdE.png" />
 - <strong>Optional two-factor authentication</strong>: Users can optionally go to their profile page and add a phone number and enable Two-Factor Authentication:
<img src="http://i.imgur.com/8pfdmG6.png" />
   When the user enters his phone number, we send an SMS verification code via your developer Twilio account:
<img src="http://i.imgur.com/XKJN82m.png" />
   With Two-Factor Authentication enabled, when the user goes to sign-in next time, he will first login as usual, and then be prompted to enter the 2nd form of identification, either email or SMS:
<img src="http://i.imgur.com/Ik8s6Yc.png" />
  The user will receive a verfication code via SMS or email and be redirected to the verification page:
<img src="http://i.imgur.com/ym8bFrW.png" />
  Upon entering the verification code, they'll be able to sign in.

#To run this sample:

 1. Run a RavenDB server locally on the default port (8080). Alternately, change the RavenDB connection string in web.config to point it to a database somewhere else.
 2. Get a SendGrid account. <a href="https://sendgrid.com/transactional-email/pricing">Sign up here</a> for a free 200 emails/day account.
 3. Get a Twilio account. <a href="https://www.twilio.com/try-twilio">Sign up here</a> for a free account.
 4. Create an empty file in the RavenDB.ModernMvcStarterKit\RavenStarterKit directory, name it AppSettingsSecrets.config.ignore
 5. Put your Twilio and SendGrid credentials in AppSettingsSecrets.config.ignore, so that it looks like this:
<pre>
   &lt;appsettings&gt;    
      &lt;!-- SendGrid--&gt; 
      &lt;add key="mailAccount" value="SendGrid account ID" /&gt;
      &lt;add key="mailPassword" value="SendGrid password" /&gt;
   
      &lt;!-- Twilio--&gt; 
      &lt;add key="TwilioSid" value="Twilio SID" /&gt;
      &lt;add key="TwilioToken" value="Twilio secret token" /&gt;
      &lt;add key="TwilioFromPhone" value="Twilio number here, e.g. +13334444333" /&gt; 
   &lt;/appsettings&gt;
</pre>

That's it! You now have an MVC site with RavenDB, user registrations with email confirmation, plus optional Two-Factor Authentication. 

Have fun!

Questions? I'm <a href="https://twitter.com/judahgabriel">@judahgabriel</a> on Twitter.