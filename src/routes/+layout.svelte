<script lang="ts">
  import { onMount } from 'svelte';
  import { browser } from '$app/environment';
  import '../app.scss';
  import Theme from '$lib/Theme.svelte';
  import Nav from '$lib/Nav/index.svelte';
  import Preload from '$lib/Preload.svelte';
  import FillAvailable from '$lib/FillAvailable.svelte';
  import StatusUpdate from '$lib/StatusUpdate.svelte';
  import { goto } from '$app/navigation';

  $: browser &&
    window.location.pathname.endsWith('/') &&
    goto(window.location.pathname.slice(0, -1) + window.location.search);

  onMount(() => import('@webcomponents/webcomponentsjs/webcomponents-bundle.js'));
</script>

<FillAvailable />
<StatusUpdate />
<Theme />
<Preload />

<Nav />

<main id="main-content">
  <slot />
</main>

<style global lang="scss">
  .material-icons.external-link {
    font-size: 0.75em;
    opacity: 0.75;
  }
  body:not(.black) sl-input[filled] {
    caret-color: var(--sl-input-color) !important;
    --sl-input-background-color-hover: var(
      --sl-input-filled-background-color
    ) !important; // https://github.com/shoelace-style/shoelace/pull/644/commits/85b5d6db1a9b9804a9e924acc71a5319b555b1ba
  }
  body {
    --vh: 1vh;
    margin: 0;
    padding: 0;
    min-height: 100vh;
    min-height: calc(100 * var(--vh));
    min-height: -webkit-fill-available;
    font-family: 'Roboto', sans-serif;
    --style-transition: background-color 200ms, color 200ms;
    transition: var(--style-transition);
  }

  main {
    min-height: 100vh;
    padding: 0px 1em;
    margin-bottom: 4rem;
  }

  @media screen and (min-width: $br-md) {
    main {
      margin-left: 5rem;
      margin-bottom: 0;
    }
  }
  // @media screen and (min-width: $br-lg) {
  //   main {
  //     //   margin-right: 5rem;
  //   }
  // }
  @media screen and (min-width: $br-xl) {
    main {
      margin-left: 16rem;
      //    margin-right: 5rem;
    }
  }

  .preload,
  .preload * {
    transition: none !important;
  }
</style>
