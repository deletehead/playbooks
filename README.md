# Playbooks
## Intro
I've helped a number of friends with information security incidents over the last year or two (compromised emails, malware, etc.). Being an offensive-focused security guy rather than defensive, I wanted a place to keep track of checklists when I encounter these issues.

# Compromised Email Account
- [ ] Change password
- [ ] Configure 2FA
- [ ] Identify active sessions. Kill any suspicious ones. If you can't identify any offending ones, just kill them all for good measure
  - Gmail: https://myaccount.google.com/device-activity
  - M365 (or O365 or whatever the kids call it these days): TODO
- [ ] Check for forwarding rules. Check again periodically to see if anything new is configured OR re-configured
  - If you see it incessantly get re-configured to send to the bad address, then go in the Inspector and copy the request as a cURL and then throw it in a shell script to submit every few seconds
- [ ] Check for recently deleted emails (ex. "New Sign-In Attempts")
  - Check if you can recover deleted emails from the trash, the attacker may have emptied the trash
- [ ] Check for recently sent emails (ex. scam emails sent to the contacts)
  - Consider reaching out to any recipients and telling them if needed
