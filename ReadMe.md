# Mobile Cryptochat

This project is currently trying to create a mobile-friendly portable version of [Open Cryptochat](https://github.com/triestpa/Open-Cryptochat) which will eventually run on TOR. 
Ideally this will constist of a Cordova app along with a runnable server instance, either directly from Termux and with TOR or with a seperate server instace.

So far there is:

- WIP: create a Cordova container
- WIP: Research on how to run NodeJS server from Android


# Wiki

## Mobile Server

### Get the tools

To get most things running on the Android phone we can use [Termux](https://termux.com/). 
- Install it from playstore
- Open, type
```
pkg upgrade
pkg install vim git nodejs tor torsocks
```

### Create a hidden service

For this to work you need all the tools installed. 
- `vim $PREFIX/etc/tor/torrc`
- uncomment and edit these lines (should be ln 72-73) by 
```
#HiddenServiceDir /usr/local/var/lib/tor/hidden_service/
#HiddenServicePort 3000 127.0.0.1:80
```
- (`3000` specifies the port on which the server instance of your app is running. For this project this is `3000`. Port `80` is the port on which the service will be exposed to the outside.)
- Save and quit
- run `tor`
- If successful, open new termux session
- `cat <HiddenServiceDir>/hostname` should output sth like this: `g3yv3tvqrbow7koz.onion`

References: 
[Termux Remote Access](https://wiki.termux.com/wiki/Remote_Access#Installing_needed_packages)
[Tutorial](https://glow.li/technology/2015/11/06/run-an-ssh-server-on-your-android-with-termux/)

