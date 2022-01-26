<h1>Friend Tracker</h1>
<WelcomeMessage name="Shaun" />
<ProfileInfo person={person} />

<script>
import WelcomeMessage from './WelcomeMessage.svelte';
import ProfileInfo from './ProfileInfo.svelte';

let person = {
	name: 'Shaun Wassell',
	age: 120,
	bio: 'I like to program. I also like food.',
	birthday:  'March 1',
	interests: ['Programming', 'Data Science', 'Gardening', 'Foreign Languages'],
	imageSrc: 'images/my-profile-pic.png',
	imageAlt: 'Shaun smiling',
}
</script>
