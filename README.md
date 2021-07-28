# How to run Guacamole on CapRover

If you do not know about Guacamole or CapRover, check them out:

[![Website](https://img.shields.io/website?label=Guacamole&style=for-the-badge&url=https%3A%2F%2Fguacamole.apache.org)](https://guacamole.apache.org/)

[![Website](https://img.shields.io/website?label=CapRover&style=for-the-badge&url=https%3A%2F%2Fcaprover.com)](https://caprover.com//)

### Process
 1. [Set up CapRover](https://caprover.com/docs/get-started.html) - The simplest way to do this is with DigitalOcean; if you'd like, you can use my affiliate link:
 [![DigitalOcean Referral Badge](https://web-platforms.sfo2.digitaloceanspaces.com/WWW/Badge%203.svg)](https://www.digitalocean.com/?refcode=58f36877a0c2&utm_campaign=Referral_Invite&utm_medium=Referral_Program&utm_source=badge)
 2. Use the one-click-app - In your CapRover instance, go to `Apps > One-Click Apps/Databases > Guacamole`. Enter your app name (probably `guacamole`) and database password. Deploy the app.
 3. Enable `https` and `websocket support` in the `guacamole` dashboard (in CapRover). You may want to also enable `force https`.
 4. Set up the database - Guacamole does not automatically configure the database (unlike many other One-Click Apps, which do). You will need to connect to your MySQL database to run two SQL scripts. I suggest you create another One-Click App, `adminer`. In Adminer (after it is deployed), or whichever SQL client you choose to use, go to the `guacamole` database and find the `SQL Command` dashboard. Copy and paste and execute each of these scripts:
   - [create-schema.sql](https://raw.githubusercontent.com/apache/guacamole-client/master/extensions/guacamole-auth-jdbc/modules/guacamole-auth-jdbc-mysql/schema/001-create-schema.sql)
   - [create-admin-user.sql](https://raw.githubusercontent.com/apache/guacamole-client/master/extensions/guacamole-auth-jdbc/modules/guacamole-auth-jdbc-mysql/schema/002-create-admin-user.sql)
 5. Give `guacamole` a moment, and then it should be ready. You can access `guacamole` by going to the domain assigned to it with `/guacamole` on the end (eg: `https://${appname}.yourdomain.com/guacamole`). The default username is `guacadmin` and the default password is also `guacadmin`. I recommend changing it once you log in.
 6. (Optional) Remove `adminer` from your CapRover instance.

_If this was helpful, consider following me on Github or giving this repository a star. Thank you._
