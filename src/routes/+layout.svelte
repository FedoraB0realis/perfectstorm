<script lang="ts">
  import "../app.postcss";
  import { AppShell, AppBar } from "@skeletonlabs/skeleton";
  import Navigation from "$lib/components/Navigation.svelte";
  import logo from "$lib/assets/logo.png";
  import {
    initializeStores,
    Drawer,
    getDrawerStore,
  } from "@skeletonlabs/skeleton";

  initializeStores();

  const drawerStore = getDrawerStore();

  function drawerOpen(): void {
    drawerStore.open({});
  }
</script>

<Drawer>
  <Navigation />
</Drawer>
<!-- App Shell -->
<AppShell>
  <svelte:fragment slot="header">
    <!-- App Bar -->
    <AppBar shadow="drop-shadow-2xl" background="variant-glass-surface">
      <svelte:fragment slot="lead">
        <div class="">
          <button class="lg:hidden btn btn-sm mr-4" on:click={drawerOpen}>
            <span>
              <svg viewBox="0 0 100 80" class="fill-token w-4 h-4">
                <rect width="100" height="20" />
                <rect y="30" width="100" height="20" />
                <rect y="60" width="100" height="20" />
              </svg>
            </span>
          </button>
          <!-- <a class="hidden sm:flex btn btn-md variant-glass-primary" href="/" -->
          <!--   ><strong class="text-xl uppercase">Perfect Storm</strong></a -->
          <!-- > -->
          <a class="hidden sm:flex" href="/"><img src={logo} alt="pflogo" /></a>
        </div></svelte:fragment
      >
      <svelte:fragment slot="default">
        <nav class="list-nav">
          <ul
            class="hidden lg:flex flex-wrap justify-center items-center text-6xl"
          >
            <li class="hidden"></li>
            <li class=""><a href="/events">Events</a></li>
            <li class=""><a href="/games">Games</a></li>
            <li class=""><a href="/schedule">Schedule</a></li>
            <li class=""><a href="/venue">Venue</a></li>
            <li class=""><a href="/contact">Contact</a></li>
          </ul>
        </nav>
      </svelte:fragment>
      <svelte:fragment slot="trail">
        <a
          class="btn btn-lg variant-glass-secondary text-4xl mr-8"
          href="https://www.start.gg/tournament/perfect-storm-2025"
          target="_blank"
          rel="noreferrer"
        >
          Sign Up
        </a>
      </svelte:fragment>
    </AppBar>
  </svelte:fragment>
  <!-- Page Route Content -->
  <div class="pt-4">
    <slot />
  </div>
</AppShell>
