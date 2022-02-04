<ProfileInfo person={friend} />

<script>
import { useParams } from 'svelte-navigator';
import ProfileInfo from '../ProfileInfo.svelte';
import { friendsData } from '../data';

const params = useParams();

let friend = friendsData.find(friend => friend.id === $params.friendId);
</script>