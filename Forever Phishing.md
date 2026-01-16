As long as the internet exists, there will always be someone out there phishing for your information.

Quick phishing refresher:
1. Phishing comes in many names ( Vishing, smishing, spear phishing, whaling, quishing...etc)
2. No matter the name, the goal is to attempt to steal information from someone or get someone to do something that compromises their technology.
3. Questioning where any type of communication comes from, if not from a trusted entity is key to stopping phishing in it's tracks.

Phishing attacks can be complicated, overwhelming and very annoying, but sometimes phishing can be very simple. 
The example I have comes from a real phishing attempt I was looking into recently. 

It is early January and tax return time is coming up. As much as we are aware of important events in our lives, so are hackers. 
The attack itself was very simple, just one request and the message was generally polite and not trying to induce any type of urgency.
The email importance was marked as "high" but only to attempt to push the email through quicker.

[image]

The request was for employee's 2025 W-2 forms. Requesting they be sent back to this email. No malicious links to click, no urgency, just a message with a request. 
Simple.
The odd part of the email was where it was coming from. info@MIT.edu. The email itself met all the marks, with the exception of DKIM not passing.
The email still got through since all other aspects of the email passed and came from a legitimate email and location.

For these types of emails, it is important that your users understand that, though a message looks harmless, when anyone requests information,
especially information that has user PII, double checking is important. The attacker is hoping that someone in HR would read the email, 
and blindly just send the information they requested. Thankfully this did not happen. "Good job HR!!" 

In this instance it was brought to my attention and I had the emails removed from inboxes as quickly as possible.

Then I started my investigation.

The first thing I did, after quarentining the email, was grabbing the header because a lot of details hide in there. 

The very first thing we look at is where is this email coming from, just to verify legitimacy. We got the originating IP and could see the path it took.
The path was legitimate and the IP address was that of MIT and thanks to the MIT mail server, we could see the account that authenticated to send the email out.
This prompts us to believe that whatever account sent these out was compromised.
The next part that stood out was the "Reply-To" section. You do not always see this section, but for instances of spoofed emails or compromised accounts, 
you will often see the reply-to email being completely different from the origin email, since attackers know they wont typically have access to the account very long, 
and they don't want the information they are trying to steal to go somewhere they cant access.

What now?
There technically isn't a way to prevent these attacks from happening, from a Security perspective this is one of the accepted risks we have to assume is going to happen
maybe not frequently, but often enough to keep an eye out for them.
Some security policies could be put in place in hopes that entities like Microsoft Defender can stop some of them from going thorugh. 
for example: 
You could set a policy that prevents mass emails from targetting your company HR or payroll services email address.
You could also set a policy that can scrutinize emails with certain words in the subject and body from emails that are not normally interacting with HR or payroll services emails. "invoice, urgent, passed-due..etc)
It is very hard to stop these type of attacks through policy alone, we often have to inform the public of these types of issues to look out for.

Attackers are learning new ways to get around security policies, but sometimes even the more simple of ideas can still walk right through the door. 
Thankfully fail-safes are the best way to help in these situations.

With this example specifically a few days later, the exact same email came from an mit.edu email account again, different email address but the exact same message.
This triggered Microsoft Defender Fingerprint matching and it sent the email straight to quarentine. Regardless if the message comes from a completely different domain, 
it could be the email layout, the body text pattern, attachment hashes, embeded URLs and how they are constructed, and even CSS or layout markers.
With these indicators, it is easy to stop these attackers from overwhelming your users.










