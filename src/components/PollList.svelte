<script>
    import PollStore from '../stores/PollStore';
    import PollDetails from './PollDetails.svelte';
    export let polls = [];

    PollStore.suscribe(data => {
        polls = data;
    })
</script>

<div class="poll-list">
    {#each polls as poll (poll.id)}
        <div>
            <!--so from here we foward the click event we sent from the poll list to the app .svelte-->
              <PollDetails {poll} on:vote/>
        
        </div>
    {/each}
</div>

<!--1fr makes each grid item take half the space of the div-->
<style>
    .poll-list{
        display:grid;
        grid-template-columns: 1fr 1fr;
        grid-gap: 20px;
    }
</style>