<template>
    <div>
        <h1>DadJokes jokes</h1>   
        <Searchjokes v-on:search-text="searchText"/>
        <Joke v-for="joke in Jokes" :key="joke.id" :id="joke.id" :joke="joke.joke" />
      </div>
  </template>

<script>
import Joke from "../../components/joke.vue";
import Searchjokes from "../../components/searchjokes.vue";

export default {
    data() {
        return {
            Jokes: []
        };
    },
    async created() {
        const config = {
            headers: {
                Accept: "application/json"
            }
        };
        try {
            const res = await this.$axios.get(`https://icanhazdadjoke.com/search`, config);
            this.Jokes = res.data.results;
            console.log(res.data);
        }
        catch (err) {
            console.log(err);
        }
    },
    methods: {
      async searchText(text){
      // console.log(text)
      const config = {
            headers: {
                Accept: "application/json"
            }
        };
        try {
            const res = await this.$axios.get(`https://icanhazdadjoke.com/search?term=${text}`, config);
            this.Jokes = res.data.results;
            console.log(res.data);
        }
        catch (err) {
            console.log(err);
        }
      }
    },
    head() {
        return {
            title: this.joke,
            meta: [
                {
                    hid: "description",
                    name: "description",
                    content: "Best place for corny dad jokes"
                }
            ]
        };
    },
};
</script>

<style>

</style>