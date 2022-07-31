<template>
  <p>Waktu Reaksi - {{ score }} ms</p>
  <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
    props: ['score'],
    data() {
        return{
            rank: null
        }
    },
    mounted() {
        if (this.score < 250){
            this.rank = 'Mantap Banget'
        } else if (this.score < 400){
            this.rank = 'Hebat Juga'
        } else {
            this.rank = 'Lebih Cepat Lagi'
        }
    }
}
</script>

<style>
    .rank{
        font-size: 1.4em;
        color: #0faf87;
        font-weight: bold;
    }
</style>