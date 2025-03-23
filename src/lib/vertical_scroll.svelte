<script>
  import { linear, cubicOut } from 'svelte/easing'

  const {
    wordList: wordList = [""],
    preWord: preWord = "",
  } = $props()

  let words = $state([...wordList])
  let transition = false

  if (!transition) {
    transition = true

    setInterval(() => shiftWords(), 2000)
  }



  const shiftWords = () => {
    const tmpWords = [...words]

    const first = tmpWords.shift()

    tmpWords.push(first)

    words = tmpWords
  }


  const verticalAnimation = (node, { from, to }, params) => {
    return {
      delay: 0,
      duration: 1000,
      easing: linear,
      tick: (t, u) => {
        Object.assign(node.style, { transform: `translateY(-${t * 100}%)` })
      }
    }
  }
</script>

<button onclick={shiftWords}> test </button>
<div class="container">
  <p>{preWord}</p>
  <div class="words">
    {#each words as word, index (word)}
      <div class="word" animate:verticalAnimation> {word} </div>
    {/each}
  </div>
</div>


<style>
  p {
    margin: auto 0;
  }

  .container {
    color: rgb(124, 124, 124);
    font-family: "Poppins", sans-serif;
    font-weight: 500;
    font-size: 25px;
    -webkit-box-sizing: content-box;
    box-sizing: content-box;
    height: 40px;
    padding: 10px 10px;
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    border-radius: 8px;
  }

  .words {
    overflow: hidden;
    position: relative;
    display: flex;
    flex-direction: column;
  }
  .words::after {
    content: "";
    position: absolute;
    inset: 0;
  }

  .word {
    margin-top: 1px;
    padding-top: 3px;
    display: block;
    height: 100%;
    padding-left: 6px;
    transform: translateY(-100%);
  }
</style>
