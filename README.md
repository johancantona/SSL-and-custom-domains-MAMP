# SSL-and-custom-domains-MAMP
### How to add SSL to custom domains and localhost for MAMP (free version) ###

🚩 *This example is tested in MAMP 6.3 (Chrome and Safari)*

🚩 *Very important that the MAMP ports are set to 80 & 3306*

🚩 *Change the paths and the testdomain.test to whatever you want*


1. In etc/hosts point 127.0.0.1 to testdomain.test

2. Flush the DNS (Ventura) with `sudo dscacheutil -flushcache; sudo killall -HUP mDNSResponder`

3. Create a folder in Applications/MAMP named ssl. Also, open a terminal and run `mkcert --install`. If you dont have mkcert, download it with `npm install -g mkcert`.

4. Go to Applications/MAMP/ssl folder you created thru the terminal and run `mkcert testdomain.test`. If you want to force ssl on localhost aswell run `mkcert localhost` aswell. You should now have two .pem-files in the ssl-folder.

5. Open the file Applications/MAMP/conf/apache/httpd.conf and uncomment `#Include /Applications/MAMP/conf/apache/extra/httpd-vhosts.conf`

6. Replace the Applications/MAMP/conf/apache/extra/httpd-vhosts.conf file with the file in this repo. 

7. Now you have connected the created cert with a host. 

8. Restart MAMP and you should be able to enter https://testdomain.test and get a lock in the browser
