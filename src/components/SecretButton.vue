<template>
    <v-container>
        <div @click="openFullscreen" text elevation="0">
            <span>❤️</span></div>
        <div v-show="isVideoVisible" ref="fullscreenContainer" class="fullscreen-container">
            <iframe :src="videoUrl" frameborder="0" allowfullscreen></iframe>
        </div>
    </v-container>
</template>

<script>

import videoPath from '@/assets/secretvideo.mp4'

export default {
    data() {
        return {
            videoUrl: videoPath,
            isVideoVisible: false,
        }
    },
    methods: {
        openFullscreen() {
            const fullscreenContainer = this.$refs.fullscreenContainer;
            if (fullscreenContainer.requestFullscreen) {
                fullscreenContainer.requestFullscreen();
            } else if (fullscreenContainer.mozRequestFullScreen) {
                fullscreenContainer.mozRequestFullScreen();
            } else if (fullscreenContainer.webkitRequestFullscreen) {
                fullscreenContainer.webkitRequestFullscreen();
            } else if (fullscreenContainer.msRequestFullscreen) {
                fullscreenContainer.msRequestFullscreen();
            }
            this.isVideoVisible = true;
        },
    }

}

</script>

<style scoped>
.fullscreen-container {
    position: relative;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: black;
    z-index: 9999;
}

.fullscreen-container iframe {
    width: 100%;
    height: 100%;
}

</style>