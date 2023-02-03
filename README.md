# Projects
## Unnamed Multiplayer Shooter Game 
### About
In this project I made an FPS multiplayer game made in Unity. The game is a fast-paced free-for-all deathmatch in which players have two guns: a pistol and a rocket launcher. Players can propel themselves with the rockets they launch and it is a vital part of the gameplay; players must be swift in order not to explode or get shot so they should use  this movement tool. You can also climb certain walls and wall jump. I was always fond of multiplayer games and I am a fan of fast-paced multiplayer shooters like Quake so this game pays homage to them.
<img src="https://github.com/arastasci/arastasci.github.io/blob/master/arenaGifv2.gif" width=1000>
![](https://github.com/arastasci/arastasci.github.io/blob/master/arenaGifv2.gif)

### Project Overview
#### Netcode
Obviously, the trickiest part of this project was the networking solution. For the netcode, with the help of an online tutorial on socket programming, I used barebones .NET Sockets. Using classes I created named Packet (which is a class for creating, reading and writing on packet instances), Client (which contains the client endpoint and methods to receive and) and Server (which represents the server endpoint), I abstracted communicating between client and server to simply creating `PacketHandler` and `SendData` methods. 

The way the networking works is after a to-be client sends a connection request to the server via both TCP and UDP from the `Client` class and `Server` receives a callback for that, if there is space the client is placed on one of the spots in the `Server.clients` hashmap(which is a `Dictionary<int,Client>`) and its endpoint info is transferred to there. After this process, the receiving and sending of packets are handled from that `Client` instance. As the endpoints have the ability to send and receive data through TCP and UDP, I used TCP for reliable communication and UDP for fast but unreliable communication. 
The reason I created my own networking solution instead of an already available one was my desire to get a deeper understanding of how multiplayer game netcodes are made. 
<!-- I made two Unity projects: one for the server and one for the client. The reason for this is I wanted to make the game server-authoritative as it is a good practice for competitive games because of possible cheating issues. I made a Linux server build for the server and hosted a game in the cloud using AWS.  -->
#### Gameplay Programming
The movement is heavily physics based. The players have rigidbody components and forces are applied to them according to inputs and external factors (such as rocket explosions and speed boosts). The player can climb and jump off walls, crouch and slide and rocket-jump. I made a custom map suitable for this type of movement, with platforms and strategically placed walls that can be wall-jumped. I created a scoreboard in which each client can see each others' info (like username, kill, death, ping) ranked by the kill count. I also created a kill log at the top-right corner of the screen from which you can see the latest kills and its content (killer, victim, gun used). I also made a player tag which is only visible when the player is in your sight, which makes sense as this is a free-for-all. I put spawn areas in various locations and made spawners which spawn power-ups which can heal or speed up the player who picked it.

## OpenGL Game Engine (Early Development)
### About
In this still on-going project of mine I am making a mini game engine from scratch using C++ and OpenGL. I have made a model loading system using **Assimp** which can import almost any type of 3D model file. I have made use of **Phong shading** for rendering 3d objects affected by light casters. With the help of an online resource, I have also made a skeletal animation system which takes Collada (.dae) files and animates the object. I also took use of `ImGui` to make a GUI to easily manipulate variables at runtime. The current result is below:
<img src="https://github.com/arastasci/arastasci.github.io/blob/master/opengldemogif.gif" width=1000>
![](https://github.com/arastasci/arastasci.github.io/blob/master/opengldemogif.gif)
Here is a link to a full walkthrough of the project: [YouTube link](https://youtu.be/_5bF9Hu2eBs)
