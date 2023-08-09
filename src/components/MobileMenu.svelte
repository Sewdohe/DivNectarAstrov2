<script>
  import { fly, scale } from 'svelte/transition';
  import { quadOut } from 'svelte/easing';

  export let open;

  let links = [
    {display: "Home", href: "/"},
    {display: "Blog", href: "/blog"},
    {display: "CraftNectar", href: "/craftnectar"},
    {display: "About", href: "/resume"},
  ]
</script>

{#if open}
  <div class="menu">
      {#each links as link, i}
          <p transition:fly={{ y: -15, delay: 50 * i }}>
            <a href={link.href}>{link.display}</a>
          </p>
      {/each}
  </div>

  <div class="bar" transition:scale={{ duration: 750, easing: quadOut, opacity: 1 }} />
{/if}

<style>
  :global(html) {
      background: #1d1d2f;
  }
  .menu {
      text-align: center;
      font-size: 1.5em;
      letter-spacing: 0.15em;
      padding: 1em;
      padding-top: 0;
      color: #eef;
      height: 100vh;
  }
  p {
      cursor: pointer;
      width: max-content;
      margin: 1rem auto;
  }
  p:hover {
      text-decoration: underline;
  }
  .bar {
      border-style: solid;
      border-color: white;
      border-width: 1px;
      height: 0;
  }
</style>