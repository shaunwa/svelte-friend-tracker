<div class="profile-pic-container">
	<ProfilePic
		imageSrc={person.imageSrc}
		imageAlt={person.imageAlt}
		size="256px" />
</div>
<h3>Name</h3>
<p>{person.name}</p>
<h3>Age</h3>
<p>{person.age}</p>
<h3>Bio</h3>
<p>{person.bio}</p>
<h3>Birthday</h3>
<p>{person.birthday}</p>
<h3>Interests</h3>
{#each person.interests as interest (interest)}
	<Tag text={interest} />
{/each}

<script>
import ProfilePic from './ProfilePic.svelte';
import Tag from './Tag.svelte';

export let person;
</script>

<style>
h3 {
    border-bottom: 1px dotted #ccc;
}

.profile-pic-container {
	display: flex;
	justify-content: center;
}
</style>