<script>
	import Header from "./components/Header.svelte";
	import Footer from "./components/Footer.svelte";
	import CreatePollForm from "./components/CreatePollForm.svelte";
	import Tabs from "./shared/Tabs.svelte";

	let items = ['Current Polls', 'Add New Poll'];
	let activeItem = 'Current Polls';

	const tabChange = (e) => {
		activeItem = e.detail;
	}

	let polls = [
    {
      id: 1,
      question: 'Python or JavaScript?',
      answerA: 'Python',
      answerB: 'JavaScript',
      votesA: 9,
      votesB: 15,
    },
  ];

const handleAdd = (e) => {
	const poll = e.detail;
	/// the ... is a spread operator just adds everything you have in the polls object neatly I think
	polls = [poll, ...polls];
}

</script>
<Header />
<main>
	<Tabs {activeItem} {items} on:tabChange={tabChange}/>
	{#if activeItem === 'Current Polls'}
		<p>Poll list componenet goes here</p>
	{:else if activeItem === 'Add New Poll'}
		<CreatePollForm on:add={handleAdd}/>
	{/if}
</main>
<Footer />
<style>
	main {
		width: 960px;
		margin: 40px auto;
	}
</style>