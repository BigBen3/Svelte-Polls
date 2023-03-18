<script>
  import { onMount, onDestroy } from 'svelte';
  import PollStore from '../stores/pollStore.js';
  import PollDetails from './PollDetails.svelte';
  let polls = [];
  // const unsub = PollStore.subscribe(data => {
  //   console.log(data);
  //   polls = data;
  // });
  // onMount(() => {
  //   // maybe get data from a db
  //   console.log('poll list component mounted');
  // });
  // onDestroy(() => {
  //   // unsub from store
  //   console.log('poll list component destroyed');
  //   unsub();
  // });
</script>

<div class="poll-list">
     <!--access the data in the store direclty and unscirbes autmoaticaly so there are no memory leaks -->
  {#each $PollStore as poll (poll.id)}
    <div>
       <!--so from here we foward the click event we sent from the poll list to the app .svelte-->
      <PollDetails {poll} on:vote />
    </div>
  {/each}
</div>
  <!--1fr makes each grid item take half the space of the div-->
<style>
  .poll-list{
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-gap: 20px;
  }
</style>