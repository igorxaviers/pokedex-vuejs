<template>
    <a :href="'/pokemon/'+ num">
    <div class="rounded-lg p-5 flex-1 bg-gray-50 hover:bg-gray-300 hover:scale-150 break-all transition overflow-hidden cursor-pointer" >
        <Type :type="type"/>
        <div class="relative">
            <img :src="front" alt="" class="block mx-auto w-28 transition-all z-10 relative" :class="{'change': change}">
            <img :src="front" alt="" class="block mx-auto w-28 blur z-0" >
        </div>
        <!-- <button 
            class="bg-gray-200 text-gray-900 rounded-md px-3 py-1 mb-4 z-20" 
            @click="changeImg">
                <i class="fa-solid fa-arrow-rotate-left"></i> virar
        </button> -->
        <h3 class="text-2xl text-center font-bold"> {{captalizeName}}</h3>
    </div>
    </a>

</template>

<script>

import Type from './Type.vue';
export default {
    created: function() {
        this.currentImg = this.front;
    },
    data() {
        return {
            change: true,
            isFront: true,
            currentImg: ''
        };
    },
    props: {
        name: String,
        url: String,
        type: { type: String, required: true },
        front: { type: String, required: true },
        back: { type: String, required: true },
        num: { type: Number, required: true}
    },
    computed: {
        captalizeName: function() {
            return this.name.charAt(0).toUpperCase() + this.name.slice(1);
        }
    },
    methods: {
        changeImg: function() {
            console.log('change');
            if(this.isFront) {
                this.currentImg = this.back;
                this.isFront = false;
            } else {
                this.currentImg = this.front;
                this.isFront = true;
            }
        }
    },
    components: {
        Type
    }
}
</script>

<style scoped>
    .change {
        animation: rotate forwards .4s;
    }

    .blur {
        z-index: 0;
        filter: blur(6px);
        position: absolute;
        top: 85%;
        left: 50%;
        transform: scale(1.4) translate(-35%, -50%);
        opacity: 0.4;
    }



    @keyframes rotate {
        0% { filter: blur(0px); }
        60% { filter: blur(10px); }
        100% { filter: blur(0px); }
    }
</style>