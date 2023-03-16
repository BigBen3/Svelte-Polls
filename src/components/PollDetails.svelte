<script>
    import { createEventDispatcher } from 'svelte';
    import Card from '../shared/Card.svelte';


    export let poll;
    const dispatch = createEventDispatcher();
    
    
    //reactive value

    $: totalVotes = totalVotes = poll.VotesA + poll.votesB;

    const handleVote = (option, id) => {
      //when you pass in you need to do option: option , id: id but if the things you are passing in have the same name as the varaibel with the : then you can remove that and just have the variable you are passing in
      //the dispatch sends the the parent component here it would be poll list since the poll detial is nested in the poll list so we would need to listen there. 
      dispatch('vote', {option, id})
    }
</script>
<Card>
  <div class="poll">
  <h3> {poll.question}</h3>
  <p>Total votes: {totalVotes}</p>
  <div class="answer" on:click={() => handleVote('a', poll.id)}>
      <div class="percent percent-a"></div>
      <span> {poll.answerA} ({poll.votesA})</span>
  </div>
  <div class="answer" on:click={() => handleVote('b', poll.id)}>
      <div class="percent percent-b"></div>
      <span> {poll.answerB} ({poll.votesB})</span>
  </div>
</div>
</Card>



<style>
  h3{
    margin: 0 auto;
    color: #555;
  }
  p{
    margin-top: 6px;
    font-size: 14px;
    color: #aaa;
    margin-bottom: 30px;
  }
  .answer{
    background: #fafafa;
    cursor: pointer;
    margin: 10px auto;
    position: relative;
  }
  .answer:hover{
    opacity: 0.6;
  }
  span{
    display: inline-block;
    padding: 10px 20px;
  }
</style>