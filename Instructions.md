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

```

Finally, I was able to modify the file by using `nano` and entering the hashes there.

```bash

```


## Troubleshooting:

### OPI Missing:
The error exists because the software has yet to run and locate it's other "base" files. The fix is as simple as launching the program and then re-opening the Overview.opi file


![[Pasted image 20220615231746.png]]


### Make sure to pay attention to the **file path**

![[Pasted image 20220615231924.png]]


### No Password Provided:
For this error, I was able to fix it by pressing the "Test Connection" button before storing the password. This seems like a small bug.