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
            <FriendsPage />
        </Route>
        <Route path="/profile">
            <UserProfilePage />
        </Route>
        <Route path="/friends/:friendId">
            <FriendDetailPage />
        </Route>
        <Route>
            <NotFoundPage />
        </Route>
    </div>
</Router>

<script>
import { Router, Route, Link } from 'svelte-navigator';
import FriendsPage from './pages/FriendsPage.svelte';
import FriendDetailPage from './pages/FriendDetailPage.svelte';
import UserProfilePage from './pages/UserProfilePage.svelte';
import NotFoundPage from './pages/NotFoundPage.svelte';
import Redirect from './Redirect.svelte';
</script>

<style>
.content-container {
    max-width: 700px;
    margin: auto;
}
</style>
