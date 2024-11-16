# Buisness logic vuln

* when we try to login to admin panel it asks only like @dontwanncry.com can access this pannel sometimews there must be some business logic vuln when we update our personal account email to @dontwannacry.com we can access the admin pannel and can proceed to do all activities

* Tampering with the inputs : we can sometimes change password and using burp we can erase the current pasword field in the post request and put name as administrator and password as you like then we can access the admin pannel if the password is changes
* skipping steps : if there is an option to select like roles like admin or normal user we can use interceptor and deop the role request and continue without this role request in url sometimes we can bypass it and able to acess the admin pannel

* Use TRACE : TRACE ehader in http request is an request that echoback to client for diagonistic purposes.It is not always enabled in all browsers.
*  X-Content-Type-Options and Strict-Transport-Security if these are not implemeted there is a high chance of we can exploit it