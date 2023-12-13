<script>
  import { Hamburger } from 'svelte-hamburgers';
  import Menu from '../components/MobileMenu.svelte';

  let open;
</script>

<nav class="fixed w-full z-20 top-0 left-0">
  <div
    class="max-w-screen-xl flex flex-wrap items-center justify-between mx-auto p-4"
  >
    <a href="https://divnectar.com/" class="flex items-center">
      <img
        src="/images/logo.png"
        class="h-8 mr-3"
        alt="DivNectar Logo"
      />
      <span
        class="self-center text-2xl font-semibold whitespace-nowrap dark:text-white"
        >DivNectar</span
      >
    </a>
    <div class="flex-grow"></div>
    <div class="flex md:order-2 md:invisible lg:invisible">
      <Hamburger --color="white" class="md:hidden" bind:open />
    </div>
    <div
      class="items-center justify-between hidden w-full md:flex md:w-auto md:order-1"
      id="navbar-sticky"
    >
      <ul
        class="flex flex-col p-4 md:p-0 mt-4 font-medium border justify-end rounded-lg md:flex-row md:space-x-8 md:mt-0 md:border-0"
      >
        <li>
          <a href="/" class="block py-2 pl-3 pr-4" aria-current="page">Home</a>
        </li>
        <li>
          <a href="/Posts" class="block py-2 pl-3 pr-4">Blog</a>
        </li>
        <li>
          <a href="/craftnectar" class="block py-2 pl-3 pr-4">MC Server</a>
        </li>
        <li>
          <a href="/resume" class="block py-2 pl-3 pr-4">About</a>
        </li>
        <li>
          <a href="/contact" class="block py-2 pl-3 pr-4">Contact</a>
        </li>
      </ul>
    </div>
  </div>
  {#if open}
    <Menu bind:open />
  {/if}
</nav>



<style>
  nav {
    background: rgba(255, 255, 255, 0);
    backdrop-filter: blur(10px);
    border-bottom: 1px solid rgba(255, 255, 255, 0.01);
  }
</style>