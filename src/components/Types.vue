<template>
    <div class="grid gap-2 grid-cols-12 mb-8">
        <div v-for="(type, index) in types" :key="index" class="">
            <Type :type="type.name"/>
        </div>
    </div>
</template>

<script>
import Type from './Type.vue';
import axios from 'axios';
export default {
    data() {
        return {
            types: []

        };
    },
    created: async function() {
        this.baseUrl = 'https://pokeapi.co/api/v2';
        try {
            let { data } = await axios.get(`${this.baseUrl}/type`);
            this.types = data.results;
            console.log(this.types);
        } catch (error) {
            console.log(error);
        }
    },
    components: {
        Type
    }
    
}
</script>

<style>
    Type{
        font-size: 10px;
    }
</style>