{#each people as person (person.id)}
<div class="grid-item">
    <div class="card-container">
        <ProfileInfoSmall
            person={person}
            on:click={() => cardClicked(person)} />
        {#if actionText}
        <button on:click={() => buttonClicked(person)}>{actionText}</button>
        {/if}
    </div>
</div>
{/each}

<script>
import { createEventDispatcher } from 'svelte'; 
import ProfileInfoSmall from './ProfileInfoSmall.svelte';

const dispatch = createEventDispatcher();

export let people;
export let actionText;

function cardClicked(person) {
    dispatch('personClick', person);
}

function buttonClicked(person) {
    dispatch('personActionClick', person);
}
</script>

<style>
.grid-item {
    box-sizing: border-box;
    padding: 8px;
    width: 50%;
}

.card-container {
    border: 1px solid #ccc;
    border-radius: 8px;
    margin: auto;
    max-width: 800px;
    padding: 16px;
}
</style>