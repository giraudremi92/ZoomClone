<template>
<div class="container is-widescreen" >


<div class="columns">
  <div class="column is-two-thirds">
	<div class="column">
	<h1 class="title is-1">Visio App</h1>	
	</div>    
      <div class="column col3">
<div class="columns is-multiline">


  <img  src="https://bulma.io/images/placeholders/128x128.png">

  <img src="https://bulma.io/images/placeholders/128x128.png">


  <img  src="https://bulma.io/images/placeholders/128x128.png">

  <img  src="https://bulma.io/images/placeholders/128x128.png">

</div>
   </div>
  </div>

  <div class="column" style="padding: 2rem;">
	<div class="column has-text-centered col2">
	<h2 class= " title is-3"><span class="icon">
  <i class="fas fa-comment-dots"></i>
</span> Chat</h2>

	</div>	
	<div class="columns is-mobile">
      <div class="column col4" >
        <p class="col-chat" > chat messages component</p>
      </div>
    </div>
  </div>
</div>

</div>
</template>

<script>

export default {
  name: 'App',
  components: {
  }
}
</script>

<style>
@import "https://cdnjs.cloudflare.com/ajax/libs/bulma/0.9.3/css/bulma.min.css";
@import "https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/css/all.min.css";

html,body {
    background-color: red;
}

#app{
background-color: #21242C;
color: white;
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
max-height:66vh;
overflow-y: scroll;
}

img{
width: 30%;
padding: 1rem;
}
</style>
