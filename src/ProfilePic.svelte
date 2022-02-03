<div style="--size: {size}" class="profile-pic-wrap">
    <img
        class="profile-pic"
        src={imageSrc}
        alt={imageAlt} />
</div>

<script>
export let imageSrc;
export let imageAlt;
export let size;
</script>

<style>
.profile-pic-wrap {
    width: var(--size);
    height: var(--size);
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