# Instructions:
---


# Yamcsadmin:
1) Installing the Requirements.
2) Getting Started (Webserver).
3) Installing the WebClient & GUI.
4) Creating Test users and Storing Hashes.
5) Testing Connectivity with Yamcs-Webserver.


## Installing the requirements:

```bash

check the GUI readme
```


## Getting Started (WebServer): 
This is just a `proof-of-conccept` to get the `Server` running. This creates and launches the `webserver` that will allow users to use the `Yamcs-Client`

```bash
git clone https://github.com/yamcs/quickstart.git myproject
cd myproject
mvn yamcs:run
```

Once the server is up and running, check the terminal for a line that looks like this:

![[Pasted image 20220615223348.png]]
(*Note: You can always use `ctrl+f` on the `termianl` to find something in this case `8090`*)



## Installing the Web-Client & GUI:
This will install the GUI which should allow us to connect to our local Webserver. Once that's up an running I'll look to create a user. 

```bash
cd yamcsServer/yamcs-web/src/main/webapp
sudo npm install
sudo npm run build
cd -
sudo ./startupScript.sh

- or - 
cd yamcs-studio-1.6.1
sudo ./"Yamcs Studio"

```

One thing to note is that it should run the webserver on port 8090. 


## Logging via GUI:
To Login via the GUI, take note of the instance and login credentials that you created earlier. 

![[Pasted image 20220615232647.png]]


Then navigate to the following:

![[Pasted image 20220617230915.png]]

Enter the `instance`, `user` and `password` and voila!


## Finding the hash:
Now that we created the user and admin credentials, I'll need to get their hashes. I was able to find more reading the documetation [here](https://docs.yamcs.org/yamcs-server-manual/security/authmodules/yaml/). They mention that hashes are stored in the  `users.yaml` **file that creates itself upon creation of a user.**

```yaml
admin:
  password: somepassword
  superuser: true

someuser:
  displayName: Some User
  password: somepassword
  roles: [ Operator ]
```

I was not able to find the file by following the file structure listed on their getting started page. Instead I went to this path:

```bash
##The following two commands didn't find the required directory 
##find / -name "maya" 2>/dev/null
##grep -ir "maya" ./

##I personally used this 
cd Project/myproject/target/yamcs/yamcs-data/_global.rdb/ 

```

Finally, I was able to modify the file by using `nano` and entering the hashes there.

```bash
nano 000024.log       
```

```bash 
##log file contents with the hashes
?b�^N8^B^A"^@^@^@^@^@^@^@^A^@^@^@^A^L^@^@^@^Caccounts�^D^H^H^R�^A^H^F^R^Eadmin^Z
Administrator ^A(^A2^L^H建�^F^P����^A:^L^H建�^F^P����^AJ}
^Qadmin@example.com^Rf1000:6fd31d19e45f6907adba749d0531c866fcee3078e81f412e:5f7269adb4c94f67811ea6c2d9d8cecf5d19976c99e33102^X^A^R�^A^H^G^R^Dmaya^Z^Dmaya ^A(^B2^K^H�ú�^F^P���#:^K^H�>
^Gm@m.com^Rf1000:d2a3665132b342417567b376bd9f611e87b440d5f7cef165:3a2166b219095b234487dc0ce735f4ccb7b59fd2177e7f7b^X^@^R�^A^H^H^R^Dtest ^@(^B2^L^H�˿�^F^P����^AR�^A
$c1980336-6f5a-4223-b1e6-74b1be55d79a^Rf1000:1ffb836ad43076a3696de057709075540327de3b4a692a41:d7e8fbd4c609b8bcb5c34737122182599dea56c9a4af609a�^[��^[^@^A#^@^@^@^@^@^@^@^A^@^@^@^A
^@^@^@^Cgroups^B^H^E���U8^B^A$^@^@^@^@^@^@^@^A^@^@^@^A^L^@^@^@^Caccounts�^D^H^H^R�^A^H^F^R^Eadmin^Z
Administrator ^A(^A2^L^H建�^F^P����^A:^L^H建�^F^P����^AJ}
^Qadmin@example.com^Rf1000:a17bb8b41f949131ddebe35f5cc06bce555bd55bfbc8bfdb:563a7f135037a9471030318d59155a7bb6cb7e9fd8644f82^X^A^R�^A^H^G^R^Dmaya^Z^Dmaya ^A(^B2^K^H�ú�^F^P���#:^K^H�>
^Gm@m.com^Rf1000:d2a3665132b342417567b376bd9f611e87b440d5f7cef165:3a2166b219095b234487dc0ce735f4ccb7b59fd2177e7f7b^X^@^R�^A^H^H^R^Dtest ^@(^B2^L^H�˿�^F^P����^AR�^A
$c1980336-6f5a-4223-b1e6-74b1be55d79a^Rf1000:1ffb836ad43076a3696de057709075540327de3b4a692a41:d7e8fbd4c609b8bcb5c34737122182599dea56c9a4af609a����^[^@^A%^@^@^@^@^@^@^@^A^@^@^@^A
^@^@^@^Cgroups^B^H^E��<��^@^A&^@^@^@^@^@^@^@^A^@^@^@^A^P^@^@^@^F�^@^A�^??X��^@^@^@q^F^@^@^AIamApi^@^F^@^@^BUpdateUser^@^F^@^@^@guest^@^F^@^@^CUser 'admin' was changed^@^L^@^@^D^@^@^>
^O
^Dname^R^G^Z^Eadmin
^Q
^Hpassword^R^E^Z^C***����




```

The next step would be using this [link](https://docs.yamcs.org/javadoc/yamcs/latest/org/yamcs/security/PBKDF2PasswordHasher.html) to verify is a password is correct and figuring out how to hash passwords using ```yamcsadmin password-hash ```


## Troubleshooting:

### OPI Missing:
The error exists because the software has yet to run and locate it's other "base" files. The fix is as simple as launching the program and then re-opening the Overview.opi file


![[Pasted image 20220615231746.png]]


### Make sure to pay attention to the **file path**

![[Pasted image 20220615231924.png]]


### No Password Provided:
For this error, I was able to fix it by pressing the "Test Connection" button before storing the password. This seems like a small bug. If it still dowsn't work, I reinstalled the repo. 
You may also have some luck using the directions in the following link
[here](https://docs.yamcs.org/python-yamcs-client/general/ "https://docs.yamcs.org/python-yamcs-client/general/").