<h1>Friend Tracker</h1>
<div class="content-container">
    <WelcomeMessage name="Shaun" />
    <ProfileInfo person={myProfileData} />
    <div class="people-list">
        <div class="grid-item">
            <div class="card-container">
                <ProfileInfoSmall person={friendsData[0]} />
            </div>
        </div>
        <div class="grid-item">
            <div class="card-container">
                <ProfileInfoSmall person={friendsData[1]} />
            </div>
        </div>
        <div class="grid-item">
            <div class="card-container">
                <ProfileInfoSmall person={friendsData[2]} />
            </div>
        </div>
    </div>
</div>

<script>
import WelcomeMessage from './WelcomeMessage.svelte';
import ProfileInfo from './ProfileInfo.svelte';
import { myProfileData, friendsData } from './data';
import ProfileInfoSmall from './ProfileInfoSmall.svelte';
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