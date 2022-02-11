<WelcomeMessage name="Shaun" />
<h2>My Favorites</h2>
<p>You have selected {favorites.length} favorites</p>
<div class="people-list">
    <PeopleList
        people={favorites}
        actionText="Remove from Favorites"
        on:personClick={event => goToFriendDetailPage(event.detail)}
        on:personActionClick={event => toggleFavorite(event.detail)} />
</div>
<button on:click={resetFavorites}>Clear Favorites</button>
<h2>Other Friends</h2>
<div class="people-list">
    <PeopleList
        people={nonFavorites}
        actionText="Add to Favorites"
        on:personClick={event => goToFriendDetailPage(event.detail)}
        on:personActionClick={event => toggleFavorite(event.detail)} />
</div> 

<script>
import { onMount } from 'svelte';
import { navigate } from 'svelte-navigator';
import WelcomeMessage from '../WelcomeMessage.svelte';
import PeopleList from '../PeopleList.svelte';
import { friendsData } from '../data';

let favoritesIdsLoaded = false;
let favoritesIds = [];

$: favorites = favoritesIds.map(id => friendsData.find(friend => friend.id === id)); 
$: nonFavorites = friendsData.filter(friend => !favoritesIds.includes(friend.id));

$: favoritesIds, persistFavoritesIds();

function persistFavoritesIds() {
    if (favoritesIdsLoaded) {
        console.log('Updating...');
        localStorage.setItem('favoritesIds', JSON.stringify(favoritesIds));
    }
}

onMount(() => {
    favoritesIds = JSON.parse(localStorage.getItem('favoritesIds')) || [];
    favoritesIdsLoaded = true;
});

function goToFriendDetailPage(person) {
    navigate(`/friends/${person.id}`);
}

function toggleFavorite(person) {
    if (favoritesIds.includes(person.id)) {
        favoritesIds = favoritesIds.filter(id => id !== person.id);
    } else {
        favoritesIds = favoritesIds.concat(person.id);
    }
}

function resetFavorites() {
    favoritesIds = [];
}
</script>

<style>
.people-list {
    display: flex;
    flex-wrap: wrap;
}
</style>
