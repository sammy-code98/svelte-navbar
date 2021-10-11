<script>
import { onMount } from "svelte";


  export let name;

  // navigation items
  const navItem = [
    { label: "logo", href: "#" },
    { label: "Item1", href: "#" },
    { label: "Item2", href: "#" },
    { label: "Item3", href: "#" },
    { label: "Item4", href: "#" },
    { label: "Item5", href: "#" },
    { label: "Item6", href: "#" },
    { label: "Item7", href: "#" },
  ];
  // mobile icon and display menu
  let showMobileMenu = false;
  // event handler for mobile menu
  const MobileIcon = () => (showMobileMenu = !showMobileMenu);

  // Media match query handler

  const mediaQuery = (e) => {
    // mobile state resetter
    if (!e.matches) {
      showMobileMenu = false;
    }
  };
  // use the onmount hook to  attach media query listener
  onMount(()=>{
    const mediaListener =  window.matchMedia("(max-width :767px)")
    mediaListener.addListener(mediaQuery)
  })
</script>

<div>
  <nav>
    <div class="inner">
      <div on:click="{MobileIcon}" class={`mobile-icon${showMobileMenu ? " active" : ""}`}>
        <div class="center-line" />
      </div>
      <ul class={`navbar-list${showMobileMenu ? " mobile" : ""}`}>
        {#each navItem as item}
          <li><a href={item.href}>{item.label}</a></li>
        {/each}
      </ul>
    </div>
  </nav>

  <main>
    <h1>Hello {name}!</h1>
    <p>
      Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn
      how to build Svelte apps.
    </p>
  </main>
</div>

<style>
  nav {
    background-color: #3988d6;
    font-family: "Leckerli One", cursive;
    height: 45px;
    width: 100%;
    top: 0;
  }
  .inner {
    max-width: 980px;
    padding-left: 20px;
    padding-right: 20px;
    margin: auto;
    box-sizing: border-box;

    display: flex;
    align-items: center;
    height: 100%;
  }
  /* hamburger icon sytle */
  .mobile-icon {
    width: 25px;
    height: 14px;
    position: relative;
    cursor: pointer;
  }
  .mobile-icon:after,
  .mobile-icon:before,
  .center-line {
    content: "";
    position: absolute;
    width: 100%;
    height: 2px;
    background-color: #fff;
    transition: all 0.4s;
    transform-origin: center;
  }
  .mobile-icon:before,
  .center-line {
    top: 0;
  }
  .mobile-icon:after,
  .center-line {
    bottom: 0;
  }
  .mobile-icon:before {
    width: 66%;
  }
  .mobile-icon:after {
    width: 33%;
  }
  .center-line {
    margin: auto;
  }
  .mobile-icon:hover:before,
  .mobile-icon:hover:after,
  .mobile-icon.active:before,
  .mobile-icon.active:after,
  .mobile-icon.active .center-line {
    width: 100%;
  }
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
    font-family: "Leckerli One", cursive;
  }
  .mobile-icon.active:before,
  .mobile-icon.active:after {
    top: 50%;
    transform: rotate(-45deg);
  }
  .mobile-icon.active .center-line {
    transform: rotate(45deg);
  }

  /* navbar list sytle */
  .navbar-list {
    display: none;
    /* change the width to 100% if you want it to fill the  mobile screen */
    width: 50%;
    justify-content: space-between;
    margin: 0;
    padding: 0 40px;
  }
  .navbar-list.mobile {
    background-color: #3988d6;
    position: fixed;
    display: block;
    height: calc(100% - 53px);
    bottom: 0;
    left: 0;
  }
  .navbar-list li {
    list-style-type: none;
    position: relative;
  }
  .navbar-list li::before {
    content: "";
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    height: 1px;
    background-color: rgb(209, 209, 218);
  }
  .navbar-list a {
    color: #fff;
    text-decoration: none;
    display: flex;
    height: 45px;
    align-items: center;
    padding: 0 10px;
    font-size: 13px;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }
  /* media queries */
  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }

  @media only screen and (min-width: 767px) {
    .mobile-icon {
      display: none;
    }
    .navbar-list {
      display: flex;
      padding: 0;
    }
    .navbar-list a {
      display: inline-flex;
    }
  }
</style>
