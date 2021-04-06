<script>
	import Header from "./Components/header.svelte";
	import Footer from "./Components/footer.svelte";
	import Tabs from "./shared/tabs.svelte";
	import CreatePollForm from "./Components/createPollForm.svelte";
	import PollList from "./Components/pollList.svelte";

	// tabs
	let items = ["Current Polls", "Add New Poll"];
	let activeItem = "Current Polls";
	const tabChange = (e) => {
		activeItem = e.detail;
	};

	const handleAdd = (e) => {
		activeItem = "Current Polls";
	};
</script>

<Header />
<main>
	<Tabs {activeItem} {items} on:tabChange={tabChange} />
	{#if activeItem === "Current Polls"}
		<PollList />
	{:else if activeItem === "Add New Poll"}
		<CreatePollForm on:add={handleAdd} />
	{/if}
</main>
<Footer />

<style>
	main {
		max-width: 960px;
		margin: 40px auto;
	}
</style>
