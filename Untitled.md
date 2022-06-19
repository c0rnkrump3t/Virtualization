I tried to follow the instructions you sent me but I could not figure it out. 

I was able to create the yamcsadmin binary however I coud not get it to recognize the org.yamcs.cli.YamcsAdminCli class 

![[Pasted image 20220618221502.png]]


```

cd yamcsServer 
mvn clean package -Dmaven.tests.skip

cd yamcs-core/target/

cp yamcs-core-5.5.6-SNAPSHOT.jar ~

tar -xf yamcs-core-5.5.6-SNAPSHOT.jar

cd yamcs-core-5.5.6-SNAPSHOT
chmod +x yamcsadmin
./yamcsadmin
```


if i can i will just email fabia for help otherwise im not sure how to get the hash. i managed to get the hashes but not conventional way. 