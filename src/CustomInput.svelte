<script>
  export let val

  export function empty() {
    val = ''
  }
  // function setVal(e) {
  //   val = e.target.val

  // }
</script>

<input type="text" bind:value={val} >