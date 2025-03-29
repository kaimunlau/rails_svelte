<script>
	import { cn } from "$lib/utils.js";

	let {
		class: className,
    children,
		...restProps
	} = $props();
</script>

{#if children}
  <div
    class={cn(
      "text-xs text-destructive -mt-1",
      className
    )}
    {...restProps}
  >
    {@render children()}
  </div>
{:else}
  <div
    class={cn(
      "hidden",
      className
    )}
    {...restProps}
  >
  </div>
{/if}