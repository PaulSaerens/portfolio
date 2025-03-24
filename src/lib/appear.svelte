<script>
  import { onMount } from "svelte"

  const {
    children
  } = $props()

  let percent = $state(1)
  let elem = $state(null)

  const handleScroll = () => {
    const height = window.innerHeight
    const rect = elem.getBoundingClientRect()
    const max = height * 0.7
    const distance = height - max

    if (rect.top > height) {
      percent = 0
    }
    else if (rect.top < max) {
      percent = 1
    }
    else {
      const topDist = rect.top - max
      const toto = 1 - (topDist / distance)

      percent =  Math.pow(toto, 5)
    }
  }

  onMount(() => {
    handleScroll()
  })

</script>

<div bind:this={elem} style="opacity:{percent}">
  {@render children?.()}
</div>

<svelte:window onscroll={handleScroll} />

<style>
</style>
