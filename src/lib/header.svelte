<script module>
  import { onMount } from "svelte"

  let stars = $state([])

  const initStars = () => {
    const amount = Math.ceil(Math.random() * 50) + 30

    for (let i = 0; i < amount ; i++) {
      const delay = Math.ceil((Math.random() * 100) % 10)

      stars.push({
        top: Math.floor(Math.random() * 100),
        left: Math.floor(Math.random() * 100),
        delay: delay < 5 ? delay : delay,
        size: (Math.ceil(Math.random() * 10) + 1) % 4,
        animation: delay < 5 ? 'sparkling' : 'glow'
      })
    }
  }

</script>

<script>
  import Torch from "./torch.svelte"

  onMount(() => {
    initStars()
  })

  const starStyle = star => {
    const style = {
      width: `${star.size}px`,
      height: `${star.size}px`,
      position: 'absolute',
      top: `${star.top}%`,
      left: `${star.left}%`,
      'animation-duration': `${star.delay}s`,
      'animation-iteration-count': 'infinite',
      'animation-name': star.animation,
      'animation-timing-function': 'linear',
    }

    return Object.entries(style)
      .map(([key, value], index) => {
        return `${key}: ${value}`
      })
      .join(';')
  }
</script>

<div class="container">
  <div class='header-container'>
    <Torch />
  </div>
  <div>
    {#each stars as star}
    <div class='star' style={starStyle(star)}></div>
    {/each}
  </div>
</div>

<style>


  :root {
    --dark-sky: rgb(2, 3, 34);
  }

  .header-container {
    z-index: 2;
    display: flex;
    flex-direction: row;
    justify-content: end;
    width: 95%;
    height: 90%;
  }

  .star {
    background-color: rgb(246, 247, 184);
    border: 1px solid rgb(246, 247, 184);
    border-radius: 50%;
    box-shadow: 0 0 3px rgb(138, 218, 255);
  }

  .container {
    position: relative;
    background-color: var(--dark-sky);
    display: flex;
    flex-direction: row;
    height: 100%;
    width: 100%;
    justify-content: space-between;
    align-items: center;
  }

  .profile-desc {
    flex: 3;
    padding: 5px;
  }

  .profile-pic {
    flex: 1;
    height: 50%;
    width: 50%;
    object-fit: fill;
  }

  @keyframes -global-sparkling {
    0% {
      opacity: 100%;
    }

    10% {
      opacity: 80%;
    }

    20% {
      opacity: 100%;
    }

    40% {
      opacity: 100%;
    }

    50% {
      opacity: 70%;
    }

    60% {
      opacity: 100%;
    }

    90% {
      opacity: 100%;
    }

    100% {
      opacity: 60%;
    }
  }


  @keyframes -global-glow {
    0% {
      opacity: 10%;
    }

    50% {
      opacity: 100%;
    }

    100% {
      opacity: 10%;
    }
  }

</style>
