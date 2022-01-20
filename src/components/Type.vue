<template>
    <span :class="getTypeColor.bgPrimary" class="font-medium px-4 py-2 rounded-md text-white uppercase text-xs">
        <i :class="getTypeColor.icon" class="fa-solid mr-2"></i>
        {{type}}
    </span>
</template>

<script>
export default {
    created: function() {
        this.currentImg = this.front;
    },
    props: {
        type: { type: String, required: true },
    },
    computed: {
        getTypeColor: function() {
            switch(this.type) {
                case 'normal':
                    return { bgPrimary: 'bg-gray-500', bgSecondary: 'text-gray-200', icon: 'fa-bullseye' };
                case 'fighting':
                    return { bgPrimary: 'bg-red-500', bgSecondary: 'text-red-200', icon: 'fa-hand-fist' }
                case 'flying':
                    return { bgPrimary: 'bg-indigo-500', bgSecondary: 'text-indigo-200', icon: 'fa-seedling' }                    
                case 'poison':
                    return { bgPrimary: 'bg-purple-500', bgSecondary: 'text-purple-200', icon: 'fa-skull' }
                case 'ground':
                    return { bgPrimary: 'bg-yellow-700', bgSecondary: 'text-yellow-200', icon: 'fa-tree'}
                case 'rock':
                    return { bgPrimary: 'bg-gray-700', bgSecondary: 'text-gray-200', icon: 'fa-mountain' }
                case 'bug':
                    return { bgPrimary: 'bg-green-600', bgSecondary: 'text-green-200', icon: 'fa-bug'}
                case 'ghost':   
                    return { bgPrimary: 'bg-gray-500', bgSecondary: 'text-gray-200', icon: 'fa-ghost' }
                case 'steel':
                    return { bgPrimary: 'bg-gray-500', bgSecondary: 'text-gray-200', icon: 'fa-fire' } 
                case 'fire':
                    return { bgPrimary: 'bg-red-500', bgSecondary: 'text-red-200', icon: 'fa-fire' }                      
                case 'water':
                    return { bgPrimary: 'bg-blue-500', bgSecondary: 'text-blue-200', icon: 'fa-water' }                       
                case 'grass':
                    return { bgPrimary: 'bg-green-500', bgSecondary: 'text-green-200', icon: 'fa-leaf' } 
                case 'electric':
                    return { bgPrimary: 'bg-yellow-400', bgSecondary: 'text-yellow-200', icon: 'fa-bolt' } 
                case 'psychic':
                    return { bgPrimary: 'bg-purple-500', bgSecondary: 'text-purple-200', icon: 'fa-brain' } 
                case 'ice':
                    return { bgPrimary: 'bg-blue-500',bgSecondary: 'text-blue-200',icon: 'fa-snowflake' } 
                case 'dragon':
                    return { bgPrimary: 'bg-indigo-500',bgSecondary: 'text-indigo-200',icon: 'fa-dragon' } 
                case 'dark':
                    return { bgPrimary: 'bg-indigo-500',bgSecondary: 'text-indigo-200',icon: 'fa-moon' } 
                case 'fairy':
                    return { bgPrimary: 'bg-pink-500',bgSecondary: 'text-pink-200',icon: 'fa-moon' } 
                default:
                    return 'bg-gray-500';
            }
        }
    }
}
</script>

<style>

</style>