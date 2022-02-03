{#if shouldShowWelcomeMessage}
    <h2 class="welcome-message">Welcome to the Friend Tracker App, {name}!</h2>
{/if}
<button on:click={toggleWelcomeMessage}>{buttonText}</button>

<script>
export let name;

let shouldShowWelcomeMessage = true;
$: buttonText = shouldShowWelcomeMessage ? 'Hide' : 'Show';

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