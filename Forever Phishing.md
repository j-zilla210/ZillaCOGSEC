### Phishing, breaking down different types of phishing


As long as the internet exists, there will always be someone out there phishing for your information.

## Quick phishing refresher:
1. Phishing comes in many names ( Vishing, smishing, spear phishing, whaling, quishing...etc)
2. No matter the name, the goal is to attempt to steal information from someone or get someone to do something that compromises their technology.
3. Questioning where any type of communication comes from, if not from a trusted entity is key to stopping phishing in it's tracks.

Phishing attacks can be complicated, overwhelming and very annoying, but sometimes phishing can be very simple. 
The example I have comes from a real phishing attempt I was looking into recently. 

## Simple phishing attempt 

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

## Internal spoofing attempt

<img width="840" height="357" alt="image" src="https://github.com/user-attachments/assets/29e0e8b7-d8c6-4adf-b61d-2dca8f104b4f" />


Another recent example was an internal phishing attempt. Attacker spoofed multiple internal emails, sending them to a few users as well as sending some to the real email they attempted to spoof.

Due to it failing multiple checks (SPF, DKIM, and DMARC) Microsoft Defender immedietly blocked all the emails due to High-confidence Phishing. This also let us know that no internal accounts were compromised.

After verifying no account compromise, we can look deeper into what the attacker is after. 
In the email itself we see they are attempting to pretend that Office365 is requesting the user to update their credentials.

<img width="512" height="273" alt="image" src="https://github.com/user-attachments/assets/d79601c8-117a-46de-8388-cd6c92de03af" />


The link leads us to a redirect page, this can be a good or bad thing for phishing URLs.
Sometimes Defender recognizes redirects as malicious, but not always. Especially shortened links, sometimes obfuscation can hide what the final URL actually is. 
Once you are passed the redirect page you are given a fake Microsoft login page that shows the intended users email and only requests the password.
Biggest red flag?
none of the normal Microsoft links work (Forgot Password?, Other ways to sign in, the back arrow next to the email address) The only option is to select "sign in"

Normally I would never have anyone try to click around a very obvious phishing attempt, but this was for research and was done in a safe environment.

If you click on "Sign in" with nothing in the text box, it just tells you to enter your password.
If you enter anything into the text box, no matter what, it will tell you your password is wrong, over and over requesting you submit it again.

<img width="423" height="338" alt="image" src="https://github.com/user-attachments/assets/61f601d0-2419-4c11-a396-8fa03abd04cc" />


<img width="412" height="371" alt="image" src="https://github.com/user-attachments/assets/ceca03bb-089b-43df-af8a-ba36d205c799" />

The actual page had nothing immedietly malicious, other than intent to steal user credentials. 
Which should be alarming enough. 
These emails can come in many forms, even with links to google forms pages, though that are far more likely to be removed quicker by Google itself since their policies when it involves what content a forms page can have will often be triggered since these pages ask for PII. 


