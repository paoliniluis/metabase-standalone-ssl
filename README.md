# Metabase standalone

## Pre-requisites
- install Docker
- get the keytool tool (you should get it by installing Java 11)

## Steps
1) generate the keystore to store the cerficate files
```
keytool -genkey -keyalg RSA -alias localhost -keystore selfsigned.jks -validity 365 -keysize 2048
```
when asked about password use `storepass` and when asked about several inputs, always use `localhost`

when it says
```
Is CN=localhost, OU=localhost, O=localhost, L=localhost, ST=localhost, C=localhost correct?
```
you should enter "yes"

2) when you finish creating the keystore, try checking if everything is cool with the following:

`keytool -list -keystore selfsigned.jks`

you should see something similar to 
```
Keystore type: PKCS12
Keystore provider: SUN

Your keystore contains 1 entry

localhost, Apr 4, 2023, PrivateKeyEntry, 
Certificate fingerprint (SHA-256): xx:xx:xx:xx:...
```

3) run `docker compose up`

you should be able to get into Metabase by going to https://localhost:8443

## User and Pass
user: a@b.com
pass: Metabot1!