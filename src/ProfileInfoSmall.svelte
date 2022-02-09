<div class="container" on:click>
    <div class="profile-pic-left">
        <ProfilePic
            imageSrc={person.imageSrc}
            imageAlt={person.imageAlt}
            size="150px" />
    </div>
    <div class="details-container">
        <h3>Name</h3>
        <p>{person.name}</p>
        <h3>Age</h3>
        <p>{person.age}</p>
    </div>
</div>

<script>
import { Link } from 'svelte-navigator';
import ProfilePic from './ProfilePic.svelte';

export let person;
</script>

<style>
    .container {
        display: flex;
    }

    .profile-pic-left {
        align-items: center;
        flex: 1;
        display: flex;
    }

    .details-container {
        padding-left: 16px;
        flex: 1;
    }
</style>