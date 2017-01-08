# Zogger - is an IRC-logger with a web-interface

## 1) Create an empty DB
```
$ sqlite3 db.sqlite3
sqlite> create table zogger(serverName varchar(64), roomName varchar(64), ircUser varchar(64), currentTime varchar(64), ircMessage varchar(2048));
sqlite> select * from zogger;
```

## 2) Default zogger(irc-logger) settings
```
serverName = "irc.freenode.net:6667"
roomName = "#my-bot-test"
userName = "my-bot-test"
helloMsg = "ZOG is logging you"
dbPath = "db.sqlite3"
dbName = "zogger"
roomAssword = "" // Using passwordless login
assFile = "" // Password file is not used by default. It should contain password to avoid a commandline parameter being visible in "ps"
To override them, use cmdline switches:
./zogger -serverName="irc.freenode.net:6667"
It is possible to run multiple zogger instances with multiple chat rooms on multiple servers.
```

## 3) Look for some data:
```
$ sqlite3 db.sqlite3
sqlite> select * from zogger;
```

## 4) Default webzogger settings:
```
listenSocket = ":9991"
dbPath = "db.sqlite3"
dbName = "zogger"
webUser = "" // No HTTP-authentication by default
webAss = "" // No HTTP-authentication by default
webAssFile = "" // Password file is not used by default. It should contain password to avoid a commandline parameter being visible in "ps"
webCrtFile = "" // No HTTPS by default, pass your ssl certificate file here
webKeyFile = "" // No HTTPS by default, pass your ssl key file here
You can override them with cmdline switches, or just:
./webzogger
and proxy the 9991 port via your web-server frontend.
```
```
The built binary can be stripped and compressed with upx.
You can use the same password file both for webzogger and multiple zoggers, writing logs to the same database.
```
