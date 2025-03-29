<script>
  // grab page props from inertia
  import { page, Link, router } from '@inertiajs/svelte';
  import Button from "$lib/components/ui/button/button.svelte";
  import Logo from "$lib/components/logo.svelte";

  function handleLogout(event) {
    event.preventDefault();
    router.delete('/logout')
  }
</script>

<nav>
  <div class="flex items-center justify-between p-4 px-10 border-b">
    <Link href="/">
      <Logo class="h-10 w-42 text-primary" />
    </Link>
    {#if $page.props?.user}
      <Button variant="outline" onclick={handleLogout}>Log out</Button>
    {:else}
      <div class="gap-2">
        <Link href="/login">
          <Button variant="outline">Log in</Button>
        </Link>
        <Link href="/signup">
          <Button>Sign up</Button>
        </Link>
      </div>
    {/if}
  </div>
</nav>