<head>
	<link href="https://fonts.googleapis.com/css2?family=Rubik:wght@300&display=swap" rel="stylesheet">
</head>

<style>
div.app-container {
	font-family: 'Rubik', sans-serif;
}
</style> 

<script>
import STATES from '../lib/utils/states.js';
import EnterCredentials from './Components/EnterCredentials.svelte';
import ChoosePool from './Components/ChoosePool.svelte';
import ListUsers from './Components/ListUsers.svelte';

$: state = STATES.ENTER_CREDENTIALS;

const sharedData = {
	test: 'test success!'
};

function handleChangeState(event) {
	state = event.detail.newState;
}
</script>

<div class="app-container">
	<h1>Simply Cognito</h1>
	<p>This system is designed to help manage users in your cognito user pools. </p>
	{#if state === STATES.ENTER_CREDENTIALS}
		<EnterCredentials on:changeState={handleChangeState} {sharedData}/>
	{:else if state === STATES.CHOOSE_POOL}
		<ChoosePool on:changeState={handleChangeState} {sharedData}/>
	{:else if state === STATES.LIST_USERS}
		<ListUsers on:changeState={handleChangeState} {sharedData}/>
	{/if}
</div>
