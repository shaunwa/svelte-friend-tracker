<Router>
    <Link to="/">
        <h1>Friend Tracker</h1>
    </Link>
    <Link to="/profile">My Profile</Link>
    <div class="content-container">
        <Route path="/">
            <Redirect to="/friends" />
        </Route>
        <Route path="/friends">
            <FriendsPage
                friends={friendsData}
                favoritesIds={favoritesIds}
                user={myProfileData}
                on:toggleFavorite={event => toggleFavorite(event.detail)}
                on:resetFavorites={resetFavorites} />
        </Route>
        <Route path="/profile">
            <UserProfilePage
                user={myProfileData} />
        </Route>
        <Route path="/friends/:friendId">
            <FriendDetailPage
                friends={friendsData}
                favoritesIds={favoritesIds}
                on:toggleFavorite={event => toggleFavorite(event.detail)} />
        </Route>
        <Route>
            <NotFoundPage />
        </Route>
    </div>
</Router>

<script>
import { onMount } from 'svelte';
import { Router, Route, Link } from 'svelte-navigator';
import FriendsPage from './pages/FriendsPage.svelte';
import FriendDetailPage from './pages/FriendDetailPage.svelte';
import UserProfilePage from './pages/UserProfilePage.svelte';
import NotFoundPage from './pages/NotFoundPage.svelte';
import Redirect from './Redirect.svelte';
import { friendsData, myProfileData } from './data';

let favoritesIdsLoaded = false;
let favoritesIds = [];

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
.content-container {
    max-width: 700px;
    margin: auto;
}
</style>
