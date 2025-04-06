<script lang="ts">
  import { page } from '$app/state';
  import * as Sheet from "$lib/components/ui/sheet";
  import { Menu } from "lucide-svelte";

  // Use $state for reactive variables for hamburger menu
  let open = $state(false);
  
  // Use $derived for changed values
  let currentPath = $derived(page.url.pathname);

  const navItems = [
    { label: 'Home', path: '/' },
    { label: 'Player', path: '/player' },
    { label: 'Settings', path: '/settings' },
    { label: 'Analytics', path: '/analytics' },
    { label: 'About', path: '/about' },
  ];

  // Use $derived for the isActive function
  const isActive = $derived((path: string) => {
    // console.debug('[Navbar] Checking active path:', path, 'current:', currentPath);
    return path === currentPath;
  });


</script>

<!-- Mobile Menu -->
<div class="md:hidden">
  <Sheet.Root bind:open>
    <Sheet.Trigger asChild let:builder>
      <button 
        class="p-4" 
        onclick={() => {open = !open}}
        {...builder}
      >
        <Menu class="h-6 w-6" />
        <span class="sr-only">Toggle menu</span>
      </button>
    </Sheet.Trigger>
    <Sheet.Content 
      side="left" 
      class="w-64"
    >
      <nav class="flex flex-col gap-4 p-6">
        <a href="/" class="flex items-center gap-2 text-lg font-semibold">
          <span>UCSD Podcast Downloader</span>
        </a>
        {#each navItems as item}
          <a 
            href={item.path} 
            class={isActive(item.path) ? 'text-foreground' : 'text-muted-foreground hover:text-foreground'}
            aria-current={isActive(item.path) ? 'page' : undefined}
            onclick={() => open = false}
          >
            {item.label}
          </a>
        {/each}
      </nav>
    </Sheet.Content>
  </Sheet.Root>
</div>

<!-- Desktop Menu -->
<nav class="hidden flex-col gap-6 text-lg font-medium md:flex md:flex-row md:items-center md:gap-5 md:text-sm lg:gap-6 mt-3">
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
</nav>