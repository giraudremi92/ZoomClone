<template>
<div class="container is-widescreen" style="height:100vh">


<div class="columns">
  <div class="column is-two-thirds">
	<div class="column">
	<h1 class="title is-1">Company X Visio Room</h1>	
	</div>    
    <div class="columns is-mobile">
      <div class="column col3">
	<p>loOn sait depuis longtemps que travailler avec du texte lisible et contenant du sens est source de distractions, et empêche de se concentrer sur la mise en page elle-même. L'avantage du Lorem Ipsum sur un texte générique comme 'Du texte. Du texte. Du texte.' est qu'il possède une distribution de lettres plus ou moins normale, et en tout cas comparable avec celle du français standard. De nombreuses suites logicielles de mise en page ou éditeurs de sites Web ont fait du Lorem Ipsum leur faux texte par défaut, et une recherche pour 'Lorem Ipsum' vous conduira vers de nombreux sites qui n'en sont encore qu'à leur phase de construction. Plusieurs versions sont apparues avec le temps, parfois par accident, souvent intentionnellement (histoire d'y rajouter de petits clins d'oeil, voire des phrases embarassantes).rem</p>
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
.vdo-container{
}
</style>
