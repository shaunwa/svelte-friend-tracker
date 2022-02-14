{#if friend}
<ProfileInfo person={friend} />
<button on:click={() => dispatch('toggleFavorite', friend)}>{buttonText}</button>
{:else}
<FriendNotFoundPage />
{/if}

<script>
import { createEventDispatcher } from 'svelte';
import { useParams } from 'svelte-navigator';
import ProfileInfo from '../ProfileInfo.svelte';
import FriendNotFoundPage from './FriendNotFoundPage.svelte';

const dispatch = createEventDispatcher();

export let favoritesIds;
export let friends;

$: isFavorite = favoritesIds.includes($params.friendId);
$: buttonText = isFavorite ? 'Remove from favorites' : 'Add to Favorites';

const params = useParams();
let friend = friends.find(friend => friend.id === $params.friendId);
</script>