<div class="container" on:click={containerClicked}>
    <div class="profile-pic-left">
        <div class="profile-pic-wrap">
            <img
                on:click|stopPropagation={imageClicked}
                class="profile-pic"
                src={person.imageSrc}
                alt={person.imageAlt} />
        </div>
    </div>
    <div class="details-container">
        <h3>Name</h3>
        <p>{person.name}</p>
        <h3>Age</h3>
        <p>{person.age}</p>
    </div>
</div>

<script>
export let person;

function containerClicked() {
    alert('You clicked the container');
}

function imageClicked() {
    alert('You clicked the image');
}
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

    .profile-pic-wrap {
        width: 150px;
        height: 150px;
        border-radius: 50%;
        overflow: hidden;
        background-color: #aaa;
        display: inline-block;
        vertical-align: middle;
    }

    .profile-pic {
        width: 100%;
    }

    .details-container {
        padding-left: 16px;
        flex: 1;
    }
</style>