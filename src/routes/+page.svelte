<script>
  import { onMount } from "svelte";
  let activeIndex = 0;
  let menu;

  onMount(() => {
    menu = document.getElementById("menu");

    Array.from(document.getElementsByClassName("menu-item")).forEach(
      (item, index) => {
        item.onmouseover = () => {
          activeIndex = index;
        };
      }
    );
  });
</script>

<div id="menu" data-active-index={activeIndex}>
  <div id="menu-items">
    <a href="/" class="menu-item">Home</a>
    <a href="/" class="menu-item">Shop</a>
    <a href="/" class="menu-item">About</a>
    <a href="/" class="menu-item">Contact Us</a>
  </div>
  <div id="menu-background-pattern" />
  <div id="menu-background-image"></div>
</div>

<style>
  @import url("https://fonts.googleapis.com/css2?family=Ibarra+Real+Nova:wght@600&display=swap");
  :global(body) {
    background-color: rgb(20, 20, 20);
    margin: 0px;
  }

  #menu {
    height: 100vh;
    display: flex;
    align-items: center;
  }

  .menu-item {
    color: white;
    font-size: clamp(3rem, 8vh, 8rem);
    font-family: "Ibarra Real Nova", serif;

    display: block;
    text-decoration: none;
    padding: clamp(0.25rem, 0.5vw, 1rem) 0rem;
    transition: opacity 400ms ease;
  }

  #menu-items {
    margin-left: clamp(4rem, 20vh, 48rem);
    position: relative;
    z-index: 2;
  }

  #menu-items:hover > .menu-item {
    opacity: 0.3;
  }

  #menu-items:hover > .menu-item:hover {
    opacity: 1;
  }

  #menu-background-pattern {
    height: 100vh;
    width: 100vw;

    background-image: radial-gradient(
      rgba(2255, 255, 255, 0.1) 9%,
      transparent 9%
    );

    background-position: 0% 0%;
    background-size: 12vmin 12vmin;
    position: absolute;
    z-index: 1;

    transition: opacity 800ms ease, background-size 800ms ease, background-position 800ms ease;
  }

  #menu-items:hover ~ #menu-background-pattern {
    background-size: 11vmin 11vmin;
    opacity: 0.5;
  }

  #menu[data-active-index="0"] > #menu-background-pattern {
    background-position: 0% 25%;
  }

  #menu[data-active-index="1"] > #menu-background-pattern {
    background-position: 0% 50%;
  }

  #menu[data-active-index="2"] > #menu-background-pattern {
  background-position: 0% 75%;
}

  #menu[data-active-index="3"] > #menu-background-pattern {
  background-position: 0% 100%;
}

#menu-background-image {
    height: 100%;
    width: 100%;

    background-image: url("https://images.unsplash.com/photo-1497124401559-3e75ec2ed794?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxzZWFyY2h8M3x8YmF0bWFufGVufDB8fDB8fA%3D%3D&auto=format&fit=crop&w=500&q=60");
    z-index: 0;
    position: absolute;
    top: 0px;
    left: 0px;

    background-size: 110vmax;
    background-position: center 0%;
    opacity: 0.15;

    transition: opacity 800ms ease,
        background-size 800ms ease,
        background-position 800ms ease;
}

#menu-items:hover ~ #menu-background-image {
    background-size: 100vmax;
    opacity: 0.10;
  }

  #menu[data-active-index="0"] > #menu-background-image {
    background-position: 0% 25%;
  }

  #menu[data-active-index="1"] > #menu-background-image {
    background-position: 0% 50%;
  }

  #menu[data-active-index="2"] > #menu-background-image {
  background-position: 0% 75%;
}

  #menu[data-active-index="3"] > #menu-background-image {
  background-position: 0% 100%;
}


</style>
