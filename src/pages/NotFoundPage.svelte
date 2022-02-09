<h1>Uh oh! That page doesn't exist</h1>
<p>Sit tight, we'll redirect to the home page momentarily</p>

<script>
import { onMount } from 'svelte';
import { navigate } from 'svelte-navigator';

onMount(() => {
    setTimeout(() => {
        navigate('/');
    }, 2500);
});
</script>