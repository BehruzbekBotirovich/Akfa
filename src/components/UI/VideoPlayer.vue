<template>

    <div class="video-player " @click.self="$emit('videoStop')">
        <video class="video" controls autoplay>
            <source src="" type="video/mp4" />

        </video>
    </div>


</template>

<script setup>

</script>

<style scoped>
.video-player {
    width: 100%;
    height: 100vh;
    background: rgba(0, 0, 0, 0.571);
    position: fixed;
    z-index: 99;
    top: 0;
    left: 0;
    display: flex;
    align-items: center;
}

video {
    border: 5px solid #ccc;
    border-radius: 10px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    width: 60%;
    height: auto;
    margin: 0 auto;
    display: block;
}

@media only screen and (max-width:660px) {
    video {
        width: 90%;
        height: auto;
    }
}
</style>