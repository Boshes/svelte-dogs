<div class="dog">
  {#await dog}
    <h3>Loading New Dog</h3>
  {:then pic}
    <img
      src={pic}
      title="That's a nice dog"
      alt="That's a nice dog"
    />
  {:catch error}
    <h1>Error making Dog</h1>
  {/await}
</div>

<button on:click={getNewDog}>New Dog!</button>

<script>
let dog = fetchDogImage()

async function fetchDogImage () {
	const response = await fetch('https://dog.ceo/api/breeds/image/random')
	const { message, status } = await response.json()
	if (status === 'success') return message
}

function getNewDog () {
  dog = fetchDogImage()
}
</script>

<style>
.dog:before {
  content: 'WOW';
  display: block;
  font-size: 60px;
  position: absolute;
  right: 2em;
  top: 2em;
  animation: rainbow 7s infinite;
}

.dog:after {
  content: 'Wacky';
  display: block;
  font-size: 60px;
  position: absolute;
  left: 2em;
  bottom: 2em;
  animation: rainbow 7s infinite;
}

img {
  max-height: 80vh;
  max-width: 90vh;
  border: 3px rosybrown solid;
}

@-webkit-keyframes rainbow{
  0%{color: orange;}	
  10%{color: purple;}	
  20%{color: red;}
  30%{color: CadetBlue;}
  40%{color: yellow;}
  50%{color: coral;}
  60%{color: green;}
  70%{color: cyan;}
  80%{color: DeepPink;}
  90%{color: DodgerBlue;}
  100%{color: orange;}
}

/* Internet Explorer */
@-ms-keyframes rainbow{
  0%{color: orange;}	
  10%{color: purple;}	
  20%{color: red;}
  30%{color: CadetBlue;}
  40%{color: yellow;}
  50%{color: coral;}
  60%{color: green;}
  70%{color: cyan;}
  80%{color: DeepPink;}
  90%{color: DodgerBlue;}
  100%{color: orange;}
}

/* Standar Syntax */
@keyframes rainbow{
    0%{color: orange;}	
  10%{color: purple;}	
	20%{color: red;}
  30%{color: CadetBlue;}
	40%{color: yellow;}
  50%{color: coral;}
	60%{color: green;}
  70%{color: cyan;}
  80%{color: DeepPink;}
  90%{color: DodgerBlue;}
	100%{color: orange;}
}
</style>