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


```


## Getting Started (WebServer): 
This is just a `proof-of-conccept` to get the `Server` running. This creates and launches the `webserver` that will allow users to use the `Yamcs-Client`

```bash
git clone https://github.com/yamcs/quickstart.git myproject
cd myproject
mvn yamcs:run
```

Once the server is up and running, checck the terminal for a line that looks like this:

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

I was not able to find the file by following the file structure listed on their getting started page. Instead I executed this command to find it:

```bash
find / -name "maya" 2>/dev/null
grep -ir "maya" ./

##I personally used this actually lol
cd Project/myproject/target/yamcs/yamcs-data/_global.rdb/ 

```

Finally, I was able to modify the file by using `nano` and entering the hashes there.

```bash
nano 000014.log       
```

```bash 
##file contents
`D0i^S^A^A^O^@^@^@^@^@^@^@^A^@^@^@^A^L^@^@^@^Caccounts�^A^H^G^R�^A^H^F^R^Eadmin^Z
Administrator ^A(^A2^L^H建�^F^P����^A:^L^H建�^F^P����^AJ}
^Qadmin@example.com^Rf1000:6fd31d19e45f6907adba749d0531c866fcee3078e81f412e:5f7269adb4c94f67811ea6c2d9d8cecf5d19976c99e33102^X^A^R9^H^G^R^Dmaya^Z^Dmaya ^A(^B2^K^H�>
^Gm@m.com^X^@^B�o#^[^@^A^P^@^@^@^@^@^@^@^A^@^@^@^A
^@^@^@^Cgroups^B^H^E�T^F�|^A^A^Q^@^@^@^@^@^@^@^A^@^@^@^A^L^@^@^@^Caccounts�^B^H^G^R�^A^H^F^R^Eadmin^Z
Administrator ^A(^A2^L^H建�^F^P����^A:^L^H建�^F^P����^AJ}
^Qadmin@example.com^Rf1000:6fd31d19e45f6907adba749d0531c866fcee3078e81f412e:5f7269adb4c94f67811ea6c2d9d8cecf5d19976c99e33102^X^A^R�^A^H^G^R^Dmaya^Z^Dmaya ^A(^B2^K^>
^Gm@m.com^Rf1000:d2a3665132b342417567b376bd9f611e87b440d5f7cef165:3a2166b219095b234487dc0ce735f4ccb7b59fd2177e7f7b^X^@���l^[^@^A^R^@^@^@^@^@^@^@^A^@^@^@^A
^@^@^@^Cgroups^B^H^E^E�U�^V^@^A^S^@^@^@^@^@^@^@^A^@^@^@^E^A^A^A^E^B^@^@^@^F^U�^{%^@^A^T^@^@^@^@^@^@^@^A^@^@^@^E^A^F^B^A^@^@^@^F^O^H^F^P^A"      audit_log)J^\��^@^A>
^N
^Dname^R^F^Z^Dmaya
^U
^KdisplayName^R^F^Z^Dmaya
^R
^Eemail^R       ^Z^Gm@m.com
^Q
^Hpassword^R^E^Z^C***�����5���^A^A^V^@^@^@^@^@^@^@^A^@^@^@^A^L^@^@^@^Caccounts�^B^H^G^R�^A^H^F^R^Eadmin^Z
Administrator ^A(^A2^L^H建�^F^P����^A:^L^H建�^F^P����^AJ}
^Qadmin@example.com^Rf1000:6fd31d19e45f6907adba749d0531c866fcee3078e81f412e:5f7269adb4c94f67811ea6c2d9d8cecf5d19976c99e33102^X^A^R�^A^H^G^R^Dmaya^Z^Dmaya ^A(^B2^K^>
^Gm@m.com^Rf1000:d2a3665132b342417567b376bd9f611e87b440d5f7cef165:3a2166b219095b234487dc0ce735f4ccb7b59fd2177e7f7b^X^@Y�R:^[^@^A^W^@^@^@^@^@^@^@^A^@^@^@^A
^@^@^@^Cgroups^B^H^E^O��g�^A^A^X^@^@^@^@^@^@^@^A^@^@^@^A^L^@^@^@^Caccounts�^B^H^G^R�^A^H^F^R^Eadmin^Z
Administrator ^A(^A2^L^H建�^F^P����^A:^L^H建�^F^P����^AJ}
^Qadmin@example.com^Rf1000:6fd31d19e45f6907adba749d0531c866fcee3078e81f412e:5f7269adb4c94f67811ea6c2d9d8cecf5d19976c99e33102^X^A^R�^A^H^G^R^Dmaya^Z^Dmaya ^A(^B2^K^>
^Gm@m.com^Rf1000:d2a3665132b342417567b376bd9f611e87b440d5f7cef165:3a2166b219095b234487dc0ce735f4ccb7b59fd2177e7f7b^X^@�|��^[^@^A^Y^@^@^@^@^@^@^@^A^@^@^@^A
^@^@^@^Cgroups^B^H^E


```
## Troubleshooting:

### OPI Missing:
The error exists because the software has yet to run and locate it's other "base" files. The fix is as simple as launching the program and then re-opening the Overview.opi file


![[Pasted image 20220615231746.png]]


### Make sure to pay attention to the **file path**

![[Pasted image 20220615231924.png]]


### No Password Provided:
For this error, I was able to fix it by pressing the "Test Connection" button before storing the password. This seems like a small bug.