<h1>Friend Tracker</h1>
<div class="content-container">
    <WelcomeMessage name="Shaun" />
    <ProfileInfo person={myProfileData} />
    <div class="people-list">
        <PeopleList people={friendsData} />
    </div>
</div>

<script>
import WelcomeMessage from './WelcomeMessage.svelte';
import ProfileInfo from './ProfileInfo.svelte';
import PeopleList from './PeopleList.svelte';
import { myProfileData, friendsData } from './data';
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