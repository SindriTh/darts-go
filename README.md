# darts-go

## INSTALL

The dependencies are in the glide.yaml. To install them:

```bash
go mod init darts-go
go get github.com/google/uuid@0.2
go get github.com/olahol/melody
go get gopkg.in/gin-gonic/gin.v1@v1.1.4
go mod tidy
go build server.go
```

## BUILD

rPi: env GOOS=linux GOARCH=arm go build server.go

501.html, main.23d958e1.js and main.b0c96aed.css are generated from
this project: https://github.com/vassdoki/darts-x01-scoreboard

cricket.html, main.0108a0d6.js and main.c5ba90a2.js are generated from
this project: https://github.com/adamgyulavari/darts-cricket
 
## RUN
 
 Start the server command:
 
 ```bash
./server
```

## Usage

I use the domain name darts3. You may replace it with the ip address of the server:

The system consists of two different user interfaces. The game UI and the admin UI.

The game UI does not handle input from the user, only shows the data received from the
server. The game UI is at the address [http://darts3:8080/game/scoreboard](http://darts3:8080/game/scoreboard)

If there is no game started, then the game UI shows a barcode, that points to the admin UI:

![QR-Code at waiting screen](https://github.com/SindriTh/darts-go/assets/70705172/366d9dde-81d1-4660-a4d2-9f20ab5bfded)


The barcode shows the url of the admin UI:



The first step is to enter the name of the players ([http://darts3:8080/admin/setPlayer](http://darts3:8080/admin/setPlayer)):
![image](https://github.com/SindriTh/darts-go/assets/70705172/6fb544d2-a846-4809-bfa6-0ef8abf91f0b)


The start button starts the game. The admin ui will show every throw. The user can fix the
recognized score in case of a wrong recognition. The game UI will show the current status
of the game.


![UI Game Started](https://github.com/SindriTh/darts-go/assets/70705172/d0c462a7-1d0c-4100-b2bb-ba89cdbeeeed)


![UI Edit Score](https://github.com/SindriTh/darts-go/assets/70705172/9d0168a1-d089-4d9e-8441-f8faeb669eb7)


## Connecting other recognition software

This is the path for entering a recognized throw:
 
 http://darts3:8080/cam/command?num=2&modifier=1

where 

* num is a number from: [1 .. 20, 25]
* modifier is in : [-1, 0, 1, 2, 3]. 
  * 1: simple
  * 2: double
  * 3: triple
  * 0: out of bounds
  * -1: darts are removed before the third throw. This will make the game UI switch player, but not implemented yet.



