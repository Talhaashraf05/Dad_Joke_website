<template>
    <nuxt-link :to="'jokes/' + id">
    <div class="joke">
        <p>{{ joke }}</p>     
    </div>
</nuxt-link>
</template>

<script>
export default{
    name: 'joke',
    props: ['joke','id']
}
</script>

<style>
.joke{
    padding: 1rem ;
    border: 1 rem dotted #a01a1a;
    margin: 1rem 0;
}
</style>