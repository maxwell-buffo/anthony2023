<template>
    <v-container class="big-button">
        <v-row class="full-height" align="center" justify="center">
            <v-col class="big-button" cols="12" sm="6" md="4" lg="3">
                <v-btn color="red" block @click="pickCelebreationType" rounded>
                    {{ celebrationStyle }}
                </v-btn>
            </v-col>
        </v-row>
    </v-container>
</template>


<script>
import JSConfetti from 'js-confetti';


const confetti = new JSConfetti();

export default {
    props: {
        celebrationStyle: String,
    },
    methods: {
        anthonyLove() {
            confetti.addConfetti({
                emojis: ['🌈', '❤️', '⭐'],
                emojiSize: 40,
                confettiNumber: 200,
            });
        },
        anthonyLike() {
            confetti.addConfetti({
                confettiColors: ['#a864fd', '#29cdff', '#78ff44', '#ff718d', '#fdff6a'],
            });
        },
        colorBlind() {
            confetti.addConfetti({
                confettiColors: ['#F5F5F5', '#C0C0C0', '#808080', '#696969', '#A9A9A9'],
            });
        },
        pickCelebreationType() {
            if (this.celebrationStyle === "Like Anthony 👍") {
                this.anthonyLike();
            } else if (this.celebrationStyle === "Love Anthony ❤️") {
                this.anthonyLove();
            } else if (this.celebrationStyle === "Colorblind Anthony 🐶") {
                this.colorBlind();
            }
        },
    },
    created() {
        // console.log(this.celebrationStyle);
    },
};
</script>

<style scoped>
.big-button {
    height: 100%;
    width: 100%;
}

.full-height {
    height: 100%;
}



</style>
