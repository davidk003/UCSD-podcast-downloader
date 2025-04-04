<script lang="ts">
  import { page } from '$app/state';

  let path;
  $: path = page.url.pathname;

  const navItems = [
    { label: 'Home', path: '/' },
    { label: 'Player', path: '/player' },
    { label: 'Settings', path: '/settings' },
    { label: 'Analytics', path: '/analytics' },
    { label: 'About', path: '/about' },

  ];

  const isActive = (itemPath: string) => path === itemPath;
</script>

<navbar
  class="hidden flex-col gap-6 text-lg font-medium md:flex md:flex-row md:items-center md:gap-5 md:text-sm lg:gap-6 mt-3"
>
  <a href="/" class="flex items-center gap-2 text-lg font-semibold md:text-base">
    <span class="sr-only">UCSD Podcast Downloader</span>
  </a>

  {#each navItems as item}
    <a 
      href={item.path} 
      class={isActive(item.path) ? 'text-foreground transition-colors' : 'text-muted-foreground transition-colors hover:text-foreground'}
      aria-current={isActive(item.path) ? 'page' : undefined}
    >
      {item.label}
    </a>
  {/each}
</navbar>