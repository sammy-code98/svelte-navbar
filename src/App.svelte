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
</script>

<div>
  <nav>
    <div class="inner">
      <div>
        <div class="middle-line" />
      </div>
      <ul>
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
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
    font-family: "Leckerli One", cursive;
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
