{#if shouldShowWelcomeMessage}
    <h2 class="welcome-message">Welcome to the Friend Tracker App, {name}!</h2>
    <button on:click={toggleWelcomeMessage}>Hide</button>
{:else}
    <button on:click={toggleWelcomeMessage}>Show</button>
{/if}

<script>
export let name;

let shouldShowWelcomeMessage = true;

function toggleWelcomeMessage() {
    shouldShowWelcomeMessage = !shouldShowWelcomeMessage;
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