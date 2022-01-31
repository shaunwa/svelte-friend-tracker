{#each people as person (person.id)}
<div class="grid-item">
    <div class={namesOfFavorites.includes(person.name)
        ? 'favorite-card-container'
        : 'card-container'}
    >
        <ProfileInfoSmall
            person={person}
            on:click ={() => toggleFavorite(person)} />
    </div>
</div>
{/each}

<script>
import ProfileInfoSmall from './ProfileInfoSmall.svelte';

export let people;

let namesOfFavorites = [];

function toggleFavorite(person) {
    if (namesOfFavorites.includes(person.name)) {
        namesOfFavorites = namesOfFavorites.filter(name => name !== person.name);
    } else {
        namesOfFavorites = namesOfFavorites.concat(person.name);
    }

    console.log(namesOfFavorites);
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

.favorite-card-container {
    background-color: lightgreen;
    border: 1px solid green;
    border-radius: 8px;
    margin: auto;
    max-width: 800px;
    padding: 16px;
}
</style>