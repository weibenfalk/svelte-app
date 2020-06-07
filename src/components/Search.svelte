<script>
  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();

  let searchText;
  let timeOut;
  let test;

  // Computed directive
  // Reactive declaration
  $: {
    if (searchText) {
      clearTimeout(timeOut);
      timeOut = setTimeout(() => {
        dispatch('search', { searchText });
      }, 500);
    }
  }

  // const doSearch = event => {
  //   const { value } = event.target;

  //   // clearTimeout(timeOut);
  //   // timeOut = setTimeout(() => {
  //   //   dispatch('search', { value });
  //   // }, 500);
  // };
</script>

<div class="wrapper">
  <div class="content">
    <i class="fa fa-search fa-2x" name="search" />
    <input bind:value={searchText} type="text" placeholder="Search Movie" />
    <!-- <input
      bind:value={searchText}
      on:input={doSearch}
      type="text"
      placeholder="Search Movie" /> -->
  </div>
</div>

<style>
  .wrapper {
    width: 100%;
    height: 105px;
    background: #1c1c1c;
    padding: 25px 20px 0px 20px;
    box-sizing: border-box;
    color: #fff;
  }

  .content {
    max-width: 1280px;
    width: 100%;
    height: 55px;
    background: #353535;
    margin: 0 auto;
    border-radius: 40px;
    position: relative;
    color: #fff;
  }

  .fa-search {
    position: absolute;
    left: 20px;
    top: 12px;
    color: #fff;
    z-index: 1000;
  }

  input {
    font-size: 28px;
    position: absolute;
    left: 0px;
    margin: 8px 0;
    padding: 0 0 0 60px;
    border: 0;
    width: 100%;
    background: transparent;
    height: 40px;
    color: #fff;
    box-sizing: border-box;
  }

  input:focus {
    outline: none;
  }

  @media screen and (max-width: 720px) {
    input {
      font-size: 28px;
    }
  }
</style>
