<script>
  import { onMount } from 'svelte'
  import Appear from "./appear.svelte"

  export let items = []

  const getItemClass = index => {
    return index % 2 === 0 ? 'left-item' : 'right-item'
  }

  let timelineContainer
  let timelineLine

  const updateLine = () => {
    if (!timelineContainer || !timelineLine) return

    const containerRect = timelineContainer.getBoundingClientRect()
    const viewHeight = window.innerHeight
    const containerTop = containerRect.top
    const bottom = -containerRect.y + (viewHeight * 0.9)

    timelineLine.style.height = `${bottom}px`
  }

  onMount(() => {
    updateLine()
  })
</script>

<div class="timeline-container" bind:this={timelineContainer}>
  <div class="timeline-center-line-container">
    <div class="timeline-center-line" bind:this={timelineLine}></div>
  </div>

  {#each items as item, index}
    <div class="timeline-row">
        <div class="timeline-item {getItemClass(index)}">
          <Appear>
            <h3>{item.title}</h3>
            <p>{item.date}</p>
            <p>{item.description}</p>
          </Appear>
        </div>
        <div class="timeline-center">
          <Appear>
            <div class="timeline-dot"></div>
          </Appear>
        </div>
        <div class="empty-item {getItemClass(index + 1)}"></div>
    </div>
  {/each}
</div>
<svelte:window onscroll={updateLine} />

<style>
  .timeline-container {
    display: flex;
    flex-direction: column;
    width: 100%;
    position: relative;
  }

  .timeline-center-line-container {
    position: absolute;
    width: 4px;
    top: 0;
    bottom: 0;
    left: 50%;
    transform: translateX(-50%);
    z-index: 1;
  }

  .timeline-center-line {
    width: 100%;
    height: 0;
    background: linear-gradient(to bottom, #3498db 90%, rgba(52, 152, 219, 0) 100%);
  }

  .timeline-row {
    display: grid;
    grid-template-columns: 1fr 60px 1fr;
    margin-bottom: 20px;
    position: relative;
    min-height: 150px;
  }

  .timeline-center {
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .timeline-dot {
    width: 20px;
    height: 20px;
    border-radius: 50%;
    background-color: #3498db;
    z-index: 2;
  }

  .timeline-item {
    padding: 15px;
    border-radius: 8px;
    background-color: #f5f5f5;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
    margin-top: 10px;
  }

  .left-item {
    grid-column: 1;
    grid-row: 1;
    margin-right: 15px;
  }

  .right-item {
    grid-column: 3;
    grid-row: 1;
    margin-left: 15px;
  }

  .item-content {
    padding: 10px;
  }

  .empty-item {
    /* Espace vide */
  }
</style>
