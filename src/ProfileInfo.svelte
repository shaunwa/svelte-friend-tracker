<div class="profile-pic-container">
	<div class="profile-pic-inner">
		<img
			class="profile-pic"
			src={person.imageSrc}
			alt={person.imageAlt} />
	</div>
</div>
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

.profile-pic-container {
	display: flex;
	justify-content: center;
}

.profile-pic-inner {
	height: 256px;
	width: 256px;
	border-radius: 50%;
	overflow: hidden;
	background-color: #aaa;
	display: inline-block;
	vertical-align: middle;
}

.profile-pic {
	width: 100%;
}
</style>