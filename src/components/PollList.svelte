<script>
    import PollDetails from './PollDetails.svelte';
    export let polls = [];
</script>

<div class="poll-list">
    {#each polls as poll (poll.id)}
        <div>
              <PollDetails {poll}/>
        
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