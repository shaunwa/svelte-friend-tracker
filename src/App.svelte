<h1>Friend Tracker</h1>
<div class="content-container">
    <WelcomeMessage name="Shaun" />
    <ProfileInfo person={myProfileData} />
    <h2>My Favorites</h2>
    <p>You have selected {namesOfFavorites.length} favorites</p>
    <div class="people-list">
        <PeopleList
            people={favorites}
            namesOfFavorites={namesOfFavorites}
            on:personClick={event => toggleFavorite(event.detail)} />
    </div>
    <button on:click={resetFavorites}>Clear Favorites</button>
    <h2>Other Friends</h2>
    <div class="people-list">
        <PeopleList
            people={nonFavorites}
            namesOfFavorites={namesOfFavorites}
            on:personClick={event => toggleFavorite(event.detail)} />
    </div>
</div>

<script>
import WelcomeMessage from './WelcomeMessage.svelte';
import ProfileInfo from './ProfileInfo.svelte';
import PeopleList from './PeopleList.svelte';
import { myProfileData, friendsData } from './data';

let namesOfFavorites = [];
$: favorites = namesOfFavorites.map(name => friendsData.find(friend => friend.name === name)); 
$: nonFavorites = friendsData.filter(friend => !namesOfFavorites.includes(friend.name));

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
.content-container {
    max-width: 700px;
    margin: auto;
}

.people-list {
    display: flex;
    flex-wrap: wrap;
}
</style>