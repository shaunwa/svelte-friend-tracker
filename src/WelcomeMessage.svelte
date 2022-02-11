{#if shouldShowWelcomeMessage}
    <div class="welcome-message">
        <h2>Welcome to the Friend Tracker App, {name}!</h2>
        <button on:click={hide}>Hide</button>
    </div>
{/if}

<script>
import { onMount } from 'svelte';

export let name;

let shouldShowWelcomeMessage = true;

onMount(() => {
    shouldShowWelcomeMessage = localStorage.getItem('welcomeMessageHidden') !== 'true';
});

function hide() {
    shouldShowWelcomeMessage = false;
    localStorage.setItem('welcomeMessageHidden', 'true');
}

</script>

<style>
.welcome-message {
    border: 1px solid #ccc;
    border-radius: 8px;
    padding: 64px;
    text-align: center;
}
</style>