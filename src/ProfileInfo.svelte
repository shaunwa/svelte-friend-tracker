<img
	src={person.imageSrc}
	alt={person.imageAlt}
	height="200" />
<h2>My Profile</h2>
<h3>Name</h3>
<p>{person.name}</p>
<h3>Bio</h3>
<p>{person.bio}</p>
<h3>Birthday</h3>
<p>{person.birthday}</p>
<h3>Interests</h3>
<p>{person.interests.join(', ')}</p>
<h3>Age</h3>
<p>{person.age}</p>

<script>
export let person;
</script>

<style>
h3 {
    border-bottom: 1px dotted #ccc;
}
</style>