<script>
	import { onMount } from 'svelte'
	onMount(() => {
		var carousel = document.getElementById('carousel')
		var red = document.getElementById('red')
		var green = document.getElementById('green')
		var blue = document.getElementById('blue')

		carousel.addEventListener('slide.bs.carousel', function(evt) {
      switch(evt.to) {
        case "0":
          red.setAttribute('class', 'btn btn-lg btn-outline-danger active')
				  green.setAttribute('class', 'btn btn-lg btn-outline-success')
				  blue.setAttribute('class', 'btn btn-lg btn-outline-primary')
          break
        case "1":
          red.setAttribute('class', 'btn btn-lg btn-outline-danger')
				  green.setAttribute('class', 'btn btn-lg btn-outline-success active')
				  blue.setAttribute('class', 'btn btn-lg btn-outline-primary')
          break
        case "2":
          red.setAttribute('class', 'btn btn-lg btn-outline-danger')
				  green.setAttribute('class', 'btn btn-lg btn-outline-success')
				  blue.setAttribute('class', 'btn btn-lg btn-outline-primary active')
      }
		})

		var popoverTriggerList = [].slice.call(document.querySelectorAll('[data-bs-toggle="popover"]'))
		popoverTriggerList.map(function (popoverTriggerEl) {
  			new bootstrap.Popover(popoverTriggerEl)
		})
	})
</script>

<nav class="navbar navbar-dark bg-dark px-4">
  <div class="container-fluid">
    <div class="row align-items-center mx-auto">
      <div class="col me-5">
        <h1 class="text-light display-3">Colors!</h1>
      </div>
      <div class="col">
        <button id="red" class="btn btn-lg btn-outline-danger active" type="button" data-bs-target="#carousel" data-bs-slide-to="0" onclick="this.blur();" data-bs-toggle="popover" data-bs-placement="bottom" data-bs-trigger="focus" title="Red button" data-bs-content="It's red!">Red</button>
      </div>
      <div class="col">
        <button id="green" class="btn btn-lg btn-outline-success" type="button" data-bs-target="#carousel" data-bs-slide-to="1" onclick="this.blur();" data-bs-toggle="popover" data-bs-placement="bottom" data-bs-trigger="focus" title="Green button" data-bs-content="It's green!">Green</button>
      </div>
      <div class="col">
        <button id="blue" class="btn btn-lg btn-outline-primary" type="button" data-bs-target="#carousel" data-bs-slide-to="2" onclick="this.blur();" data-bs-toggle="popover" data-bs-placement="bottom" data-bs-trigger="focus" title="Blue button" data-bs-content="It's blue!">Blue</button>
      </div>
    </div>
  </div>
</nav>

<main>
  <div id="carousel" class="carousel slide carousel-fade" data-bs-ride="carousel" data-bs-pause=false>
    <div class="carousel-inner">
      <div class="carousel-item min-vh-100 bg-danger active" />
      <div class="carousel-item min-vh-100 bg-success" />
      <div class="carousel-item min-vh-100 bg-primary" />
    </div>
  </div>
</main>

<style>
  /* animated text from https://codepen.io/Gwynfor/pen/yYEWPO */
  h1 {
    color: #000;
    font-family: "montserrat";
    font-size: 3vw;
    font-weight: bold;
    letter-spacing: 1vw;
    max-width: 700px;
    text-align: center;
    background: rgba(255, 253, 160, 1);
    background: -webkit-linear-gradient(left,#00ffff 0%, #97fba0 25%, #97b1fb 50%, #00ffff 100%) repeat;
    -webkit-background-clip: text;
    -ms-background-clip: text;
    -moz-background-clip: text;
    background-clip: text;
    -webkit-text-fill-color: transparent;
    -ms-text-fill-color: transparent;
    -moz-text-fill-color: transparent;
    animation-name: masked-animation;
    animation-duration: 50s;
    animation-iteration-count: infinite;
    animation-timing-function: linear;
  }

  @keyframes masked-animation {
    0% {
      background-position: 0 0;
    }
    100% {
      background-position: -8000px -3000px;
    }
  }
</style>
