# Setting up SMTP relay for self hosted Erpnext
## Setup microsoft Relay
1. Follow instructions on official relay [configuration website](https://support.office.com/en-us/article/how-to-set-up-a-multifunction-device-or-application-to-send-email-using-office-365-69f58e99-c550-4274-ad18-c805d654b4c4?ui=en-US&rs=en-US&ad=US).
2. [Test that your web server](https://docs.microsoft.com/en-us/Exchange/mail-flow/test-smtp-with-telnet) that it is not on microsoft ban list.
3. If it doesn't work follow [troubleshooting](https://support.office.com/en-us/article/fix-issues-with-printers-scanners-and-lob-applications-that-send-email-using-office-365-c75542a8-c792-42c0-a8c5-291df987512d)
## Add relay to your site
1. Open site_config.json in the main folder of your site
2. Add following lines with correct informations. Password and user name should be left blank.

```
  "mail_server": "yourdomain-com.mail.protection.outlook.com",
  "mail_port": 25,
  "use_tls": 1,
  "mail_login": "",
  "mail_password": "",
  "auto_email_id": "no-reply@yourdomain.com",
  "email_sender_name": "Notification",
  "always_use_account_email_id_as_sender": 1
```
Mail server name can be also found in your DNS MX records inside Answer section of following command.
```
dig yourdomain.com MX
```
3. test your relay by sending some alert, notification or email a file.
4. It is important to check that all created email acounts do not have pre-set **Default Outgoing**. Otherwise this account will be used instead of one inside site_config
