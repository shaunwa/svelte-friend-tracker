<WelcomeMessage name={user.name} />
<h2>My Favorites</h2>
<p>You have selected {favorites.length} favorites</p>
<div class="people-list">
    <PeopleList
        people={favorites}
        actionText="Remove from Favorites"
        on:personClick={event => goToFriendDetailPage(event.detail)}
        on:personActionClick={event => dispatch('toggleFavorite', event.detail)} />
</div>
<button on:click={() => dispatch('resetFavorites')}>Clear Favorites</button>
<h2>Other Friends</h2>
<div class="people-list">
    <PeopleList
        people={nonFavorites}
        actionText="Add to Favorites"
        on:personClick={event => goToFriendDetailPage(event.detail)}
        on:personActionClick={event => dispatch('toggleFavorite', event.detail)} />
</div> 

<script>
import { createEventDispatcher } from 'svelte';
import { navigate } from 'svelte-navigator';
import WelcomeMessage from '../WelcomeMessage.svelte';
import PeopleList from '../PeopleList.svelte';

const dispatch = createEventDispatcher();

export let favoritesIds;
export let friends;
export let user;

$: favorites = favoritesIds.map(id => friends.find(friend => friend.id === id)); 
$: nonFavorites = friends.filter(friend => !favoritesIds.includes(friend.id));

function goToFriendDetailPage(person) {
    navigate(`/friends/${person.id}`);
}
</script>

<style>
.people-list {
    display: flex;
    flex-wrap: wrap;
}
</style>
