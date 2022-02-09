<WelcomeMessage name="Shaun" />
<h2>My Favorites</h2>
<p>You have selected {namesOfFavorites.length} favorites</p>
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
import { navigate } from 'svelte-navigator';
import WelcomeMessage from '../WelcomeMessage.svelte';
import PeopleList from '../PeopleList.svelte';
import { friendsData } from '../data';

let namesOfFavorites = [];
$: favorites = namesOfFavorites.map(name => friendsData.find(friend => friend.name === name)); 
$: nonFavorites = friendsData.filter(friend => !namesOfFavorites.includes(friend.name));

function goToFriendDetailPage(person) {
    navigate(`/friends/${person.id}`);
}

function toggleFavorite(person) {
    if (namesOfFavorites.includes(person.name)) {
        namesOfFavorites = namesOfFavorites.filter(name => name !== person.name);
    } else {
        namesOfFavorites = namesOfFavorites.concat(person.name);
    }
}

function resetFavorites() {
    namesOfFavorites = [];
}
</script>

<style>
.people-list {
    display: flex;
    flex-wrap: wrap;
}
</style>
