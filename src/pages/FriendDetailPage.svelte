{#if friend}
<ProfileInfo person={friend} />
{:else}
<FriendNotFoundPage />
{/if}

<script>
import { useParams } from 'svelte-navigator';
import ProfileInfo from '../ProfileInfo.svelte';
import FriendNotFoundPage from './FriendNotFoundPage.svelte';
import { friendsData } from '../data';

const params = useParams();

let friend = friendsData.find(friend => friend.id === $params.friendId);
</script>