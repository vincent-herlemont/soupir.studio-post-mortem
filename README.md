<p align="center">
    <img src="/resources/img/logo.png" >
</p>

<br />
<br />

# Features Overview

Goal : Audio editing like text editing.

The idea that audio editing become tedious when the audio files are too long.
In standard audio editor like [finalcut](https://www.apple.com/final-cut-pro/) or [audacity](https://www.audacityteam.org/)
you have a time/db representation of sounds, you don't know when some words has been pronounced. Soupir studio
allow to display and manipulate sounds with a text editor. 

Features :

- ✅ Record
- ✅ Text editing
  - ✅ Text Styling
- ✅ Audio editing
  - ✅ Cut
  - ✅ Delete
- ✅ Audio-text features
  - ✅ Move (drag-drop) audio tracks through the text, you can see the matching between the audio track and text in real time.
  - ✅ Auto finding and stick the audio track when the text already exist. 
  - ✅ Insert tracks previously recorded.
  
You can see in the following video some demonstration of these features.

<p align="center">
    <a href="https://www.youtube.com/watch?v=nqm_ZLvUIuU">
        <img src="/resources/img/video.png" height="300px"/>
    </a>
</p>

# Technical overview

### Client

The client side is full browser app. The main part of the project as been wrote in javascript (babel es6, with some plugins).
The small amount of functionalities has excluded Typescript. The interface is compatible with recent versions
of chromium and firefox. Recorder part embedded realtime voice detection, this one is wrote in Rust and exported in Webassembly.

### Server

The server side is a full serverless architecture using aws. The backend logic is wrote in Javascript and 
executed with lambda functions. The state of application is stored in dynamodb, and the shape of data take 
care to allow a good scale. The text chunks are stored in dynamodb and audio chunks are stored in s3.


Scaling features :
- ✅ A file can have an unlimited(un arbitrary limit was chosen) number of text characters.
- ✅ A file can have an unlimited(un arbitrary limit was chosen) number of tracks.


##### Deployment 
Is managed entirely with cloudformation, all deployment are atomic and guarantee errors reproducibility 
between builds.

#### Lang/Tools

 - Aws
   - lambda
   - dynamodb
   - cognito
   - route 53
   - api gateway
   - shield
   - s3
   - cloudformation
 - Language
   - Javascript
   - Rust

