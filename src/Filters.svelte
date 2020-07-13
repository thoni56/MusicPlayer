<script>
  import { createEventDispatcher } from "svelte";

  let search = "";
  export let player;

  $: list = player
    ? player.playlist.filter(
        (item) =>
          (item.name + item.artist)
            .toLowerCase()
            .indexOf(search.toLowerCase()) !== -1
      )
    : [];

  const dispatch = createEventDispatcher();

  function changeSong(number) {
    dispatch("changeSong", {
      index: number,
    });
  }
</script>

<div id="filters">
  <button type="button" id="buggBtn" class="btn btn-secondary genre-btn">
    Bugg
  </button>
  <button type="button" id="boogieBtn" class="btn btn-secondary genre-btn">
    Boogie
  </button>
  <button type="button" id="lindyBtn" class="btn btn-secondary genre-btn">
    Lindy
  </button>
  <button type="button" id="wcsBtn" class="btn btn-secondary genre-btn">
    WCS
  </button>
</div>
