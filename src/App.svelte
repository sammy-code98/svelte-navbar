<script>
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
</script>

<div>
  <nav>
    <div class="inner">
      <div class={`mobile-icon${showMobileMenu ? " active" : ""}`}>
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
  .center-line{
	  top: 0;
  }
  .mobile-icon:after,
  .center-line{
	  bottom: 0;
  }
  .mobile-icon:before{
	  width: 66%;
  }
  .mobile-icon:after{
	  width: 33%;
  }
  .center-line{
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

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
