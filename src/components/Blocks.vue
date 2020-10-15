<template>
    <div :class="blockStatus" class="staircase">
        <div class="row item-row">
            <div class="item-col">
                <div class="perspective">
                    <div class="cube-extended" :style="{ 'background-color': backgroundColor }"><img :src="require('../assets/fighter.png')" class="fighter" /></div>
                </div>​
            </div>
        </div>
        <BlockItem 
            v-for="item in blockItems"
            :key="item"
            :name="name"
            :color="backgroundColor"
        />

    </div>
</template>

<script>
import BlockItem from './BlockItem';

export default {
    name: "Blocks",
    props: {
        blockStatus: {
            type: String,
        },
        blockItems: {
            type: Number,
            default: 3,
        },
        name: {
            type: String,
        },
        amounts: {
            type: String,
        },
        blockColor: {
            type: String,
        }
    },

    data() {
        return {
            backgroundColor: '',
        }
    },
    
    components: {
        BlockItem
    },

    mounted() {
        this.getBackground();
    },

    methods: {
        getBackground() {
            const amnt = parseFloat(this.amounts);
            if(amnt > 0) {
                this.backgroundColor = this.blockColor;
            } else {
                this.backgroundColor = '#fff';
            }
        }
    }
}
</script>

<style>
.fighter {
    transform: scale(4.5) rotate(-40deg)!important;
    position: absolute;
    top: -81px;
    right: 49px;
    height: 48px;
    width: 27px;
    z-index: -1 !important;
}
</style>