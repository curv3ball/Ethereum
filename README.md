# Ethereum

Ethereum is an AI-Based CS:GO HVH cheat that I began development on in mid 2019. The project was originally intended to be paid client work but the client bailed half way through the early development cycle even though they had already paid me majority of the money. This cheat was supposed to be one of the early desync HVH cheats that excelled at playing with CS:GO's new and inevitable randomness. Since many people have asked me tons of questions regarding this cheat over the years, this repository will walk you through how this cheat actually works, in hopes that someone from the new era of HVH can develope something that works even beyond what mine was capable of. Enjoy![App Screenshot](https://i.imgur.com/ExDv4ob.png)
### Basic Explanation
**Server**
- AI plays CS:GO in a controlled environment, then sends records of its data to a neural network to be evaulated and compared to previous data entries, then it sends the refined data to a datastore.

**Client**
- AI grabs data from the datastore every tick and compares whats currently happening around you to datastore entries to decide how to adapt to the situation

### Detailed Explanation
**Server**
- My main issue with the server was being able to reliably and consistently send information between the client and the server with as close to no delay as possible since the game can drastically change in just a few ticks. My original idea was to just send the data back and forth like you normally would with a server-client connection but after just 2 hours of testing I realized how unreliable and inconsistent this would be because ping to the server, so i opted-out of a server and began running the AI and Neural network training off of localhost. This caused more issues because now your host machine has to offload resorces to be able to train while you are playing which caused instability within CS:GO and just made the entire experience unbearable. I then started researching ways of speeding up training mechanics of a neural network without loss of hardware efficiency and I stumbled upon a [PDF](https://static.googleusercontent.com/media/research.google.com/en//pubs/archive/37631.pdf) that outlines how to speed up neural networks on CPUs, written by three people who work for Google. I was able to speed up the nerual network by using intrinsics (outlined in the PDF section 3.3) but I still needed more efficiency to keep up with the erratic changes within realtime CS:GO. I fully opted-out of using CPUs and began using a dual-GPU setup to process the AI's behavior as well as train the Nerual Network with ease without effecting game performance.
- I began learning how to use the Source SDK to actually create a map. I wanted to design a map that the AI would be able to train all aspects of CS:GO HVH on like movement prediction, lag compensation, wall checks, accuracy, as well as how hitboxes and bones work. I will not go into details about this portion nor will I release the map I created for testing but [here](https://www.youtube.com/watch?v=dhcoHQcrYKA) is an amazing resource to learn about how to make a map for testing.

<details>
  <summary> <a href="#">Make a CS:GO SDK Project</a> </summary>

- ![Make a CS:GO SDK Project](https://i.imgur.com/rZuttub.png)
</details>

<details>
  <summary> <a href="#">Make a room with 2 Bots</a> </summary>
  
- ![Make a room with 2 bots](https://i.imgur.com/qXILCax.png)
</details>

<details>
  <summary> <a href="#">Add various objects to the map (walls, ramps, headglitches)</a> </summary>
  
- ![Add objects](https://i.imgur.com/Et1yfDR.png)
</details>

<details>
  <summary> <a href="#">Compile and Test</a> </summary>
  
- ![Compile and Test](https://i.imgur.com/FMl20Od.jpeg)
</details>

- This is the map your AI will be constantly playing on to train the Neural Network
