<template>


<div class="container is-widescreen" >


<div class="columns">
  <div class="column is-two-thirds">
	<div class="column">
	<h1 class="title is-1">Visio App</h1>	
	<div class="level">
	<div class="level-left">
 <button   id="invited" class="button is-success is-outlined is-right">
    <span class="icon is-small">
      <i class="fas fa-plus"></i>
    </span>
    <span>Invite</span>
  </button>
	</div>    
<div class="level-item">
  <button class="button is-info">Join</button>
</div>

<div class="level-right">
 <button id="invited" class="button is-static is-success is-inverted is-outlined is-right">
    <span class="icon is-small">
      <i class="fas fa-user-friends"></i>
    </span>
    <span>10</span>
  </button>

</div>
</div>

</div>
     <div class="column col3">
<div id="usersplace" class="columns is-multiline">


<div id="local"></div>


</div>
   </div>

<div class="level">

<div class="level-item">
 <button @click="sharescreen" id="invited" class="button  is-success is-inverted is-outlined is-large ">
    <span class="icon">
      <i class="fas fa-volume-up"></i>
    </span>
  </button>


</div>

<div class="level-item">
 <button @click="mutevideo" id="invited" class="button  is-success is-inverted is-outlined is-large ">
    <span class="icon">
      <i class="fas fa-desktop"></i>
    </span>
  </button>



</div>

<div @click="muteaudio" class="level-item">
 <button id="invited" class="button is-success is-inverted is-outlined is-large ">
    <span class="icon">
      <i class="fas fa-microphone"></i>
    </span>
  </button>


</div>

</div>

  </div>

  <div class="column" style="padding: 2rem;">
	<div class="column has-text-centered col2">
	<h2 class= " title is-3"><span class="icon">
  <i class="fas fa-comment-dots"></i>
</span> Chat</h2>

	</div>	
	
	<div class="column col-chat" >
	
	<div class="notification">
		<div class="title is-4">13245679812345</div>
		<p>jje ne suis pas sur que le mot anticonstitutionnelemnt rentre bien</p>
	</div>

<div class="notification">
  <button class="delete"></button>
  Lorem ipsum dolor sit amet, consectetur
  adipiscing elit lorem ipsum dolor. <strong>Pellentesque risus mi</strong>, tempus quis placerat ut, porta nec nulla. Vestibulum rhoncus ac ex sit amet fringilla. Nullam gravida purus diam, et dictum <a>felis venenatis</a> efficitur.
</div>


<div class="notification">
  <button class="delete"></button>
  Lorem ipsum dolor sit amet, consectetur
  adipiscing elit lorem ipsum dolor. <strong>Pellentesque risus mi</strong>, tempus quis placerat ut, porta nec nulla. Vestibulum rhoncus ac ex sit amet fringilla. Nullam gravida purus diam, et dictum <a>felis venenatis</a> efficitur.
</div>

<div class="notification">
  <button class="delete"></button>
  Lorem ipsum dolor sit amet, consectetur
  adipiscing elit lorem ipsum dolor. <strong>Pellentesque risus mi</strong>, tempus quis placerat ut, porta nec nulla. Vestibulum rhoncus ac ex sit amet fringilla. Nullam gravida purus diam, et dictum <a>felis venenatis</a> efficitur.
</div>

<div class="notification">
  <button class="delete"></button>
  Lorem ipsum dolor sit amet, consectetur
  adipiscing elit lorem ipsum dolor. <strong>Pellentesque risus mi</strong>, tempus quis placerat ut, porta nec nulla. Vestibulum rhoncus ac ex sit amet fringilla. Nullam gravida purus diam, et dictum <a>felis venenatis</a> efficitur.
</div>
	</div>

	<div class="column col-input">
<div class="field has-addons">
  <div class="control">
    <input class="input" type="text" placeholder="Type a message">
  </div>
  <div class="control">
    <a class="button is-success">
     Send
    </a>
  </div>
</div>

	</div>

  </div>
</div>

</div>
</template>



<script>

import * as Video from 'twilio-video';

let room;



export default {
  name: 'App',
mounted(){


function connect() {
let username = 'user' + Math.floor(Math.random() * 100);


    let promise = new Promise((resolve, reject) => {
        // get a token from the back end
        let data;
        fetch('login', {
            method: 'POST',
            body: JSON.stringify({'username': username})
        }).then(res => res.json()).then(_data => {
            // join video call
            data = _data;
            return Video.connect(data.token);
        }).then(_room => {
            room = _room;
		console.log('connected to room')
            room.participants.forEach(participantConnected);
            room.on('participantConnected', participantConnected);
            room.on('participantDisconnected', participantDisconnected);
            resolve();
        }).catch(e => {
            console.log(e);
            reject();
        });
    });
    return promise;
}


connect()


function participantConnected(participant) {
  console.log('Participant "%s" connected', participant.identity);

  const div = document.createElement('div');
const usersplace = document.getElementById('usersplace');
  div.id = participant.sid;
  //div.innerText = participant.identity;
div.classList.add('userscam');
  participant.on('trackSubscribed', track => trackSubscribed(div, track));
  participant.on('trackUnsubscribed', trackUnsubscribed);

  participant.tracks.forEach(publication => {
    if (publication.isSubscribed) {
      trackSubscribed(div, publication.track);
    }
  });

  usersplace.appendChild(div);
}

function participantDisconnected(participant) {
  console.log('Participant "%s" disconnected', participant.identity);
  document.getElementById(participant.sid).remove();
}

function trackSubscribed(div, track) {
  div.appendChild(track.attach());
}

function trackUnsubscribed(track) {
  track.detach().forEach(element => element.remove());
}

function addLocalVideo() {
        Video.createLocalVideoTrack().then(track => {
        let video = document.getElementById('local');
        let trackElement = track.attach();
        video.appendChild(trackElement);
    });
}

addLocalVideo()

},

methods:{

muteaudio: function(){

room.localParticipant.audioTracks.forEach(publication => {
  publication.track.disable();
});      
},

mutevideo: function(){

room.localParticipant.videoTracks.forEach(publication => {
  publication.track.disable();
});      
},

sharescreen: async function(){
const stream = await navigator.mediaDevices.getDisplayMedia();
const screenTrack = new Video.LocalVideoTrack(stream.getTracks()[0]);



room.localParticipant.publishTrack(screenTrack);
	}
 }
}	
</script>

<style>
@import "https://cdnjs.cloudflare.com/ajax/libs/bulma/0.9.3/css/bulma.min.css";
@import "https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/css/all.min.css";

html,body {
background-color: #21242C;


}

#app{
background-color: #21242C;
}

.title{
color:white;
}

.col2{
background-color: #10B665;
border-radius: 10px;
}

.col1{
padding-top: 2rem;
}

.col3{
margin-top:3rem;
background-color:#191B1F;
border-radius: 5px;
}


.col4{
margin-top: 3rem;
}


.col-chat{
max-height:70vh;
overflow-y: scroll;
margin-top: 3rem;
}

.col-input{
margin-top:1rem;

}

img{
width: 33%;
padding: 1rem;
}

.level{
margin-top:0.6rem;

}

#local{
width:33%;
padding: 1rem;

}

.userscam{
width:33%;
padding: 1rem;
}
</style>
