# Playbooks
## Intro
I've helped a number of friends with information security incidents over the last year or two (compromised emails, malware, etc.). Being an offensive-focused security guy rather than defensive, I wanted a place to keep track of checklists when I encounter these issues.

This is focused more on home networks and personal devices/accounts, not enterprise environments.

## Compromised Email Account
- [ ] Change password
- [ ] Configure 2FA
- [ ] Identify active sessions. Kill any suspicious ones. If you can't identify any offending ones, just kill them all for good measure
  - Gmail: https://myaccount.google.com/device-activity
  - M365 (or O365 or whatever the kids call it these days): TODO
- [ ] Check for forwarding rules. Check again periodically to see if anything new is configured OR re-configured
  - If you see it incessantly get re-configured to send to the bad address, then go in the Inspector and copy the request as a cURL and then throw it in a shell script to submit every few seconds
- [ ] Check other settings such as auto reply, etc for additional modifications
- [ ] Check for recently deleted emails (ex. "New Sign-In Attempts")
  - See if the attacker initiated any password resets for other services (bank, PayPal, etc.)
  - Check if you can recover deleted emails from the trash, the attacker may have emptied the trash
- [ ] Check for recently sent emails (ex. scam emails sent to the contacts)
  - Consider reaching out to any recipients and telling them if needed
  - Consider if you need to reach out to contacts and inform them
- [ ] Reach out to the email provider and  inform them of the incident
  - I have had poor success with this, though -- typically providers won't be that helpful or extremely difficult to work with
- [ ] Scan affected device with AV
- [ ] Consider changing passwords/creds for other sites & enabling 2FA
- [ ] Set up credit monitoring for the affected party, especially if any emails in the inbox contain PII of any kind

## Suspected Malware
- [ ] Isolate/disconnect from network
- [ ] Update AV software and kick off an AV scan, clean any identified files
- [ ] For any identified malware, do quick research to identify the typical behavior of the malware
- [ ] Check version/patch level of device
- [ ] Close all applications
- [ ] Get process listing (`Get-Process` or `ps -ef`) and identify any strange/rogue processes
- [ ] Get list of network connections (`netstat`), with associated process (`-antup`)
- [ ] Check downloads folder for suspicious files
- [ ] Check other connected devices in the case of lateral movement
- [ ] Check for recently created/modified files (may be a lot of noise here)
- [ ] Reset creds where applicable and 

## Ransomware
- [ ] Isolate/disconnect from network
- [ ] Check if decryption keys are made public: https://noransom.kaspersky.com/
- [ ] As per FBI, do not pay ransom as there is no guarantee that it will work
- [ ] Reload the OS and restore from the backups that SURELY exist
