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
            v-for="(item, i) in blockItems"
            :key="item"
            :name="sampleData.PaymentDigests[i].Name"
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
            sampleData: {
                "PaymentDigests": [
                    {
                        "Id":3549478,
                        "Title":"",
                        "Description":"Tax Deductible Donation",
                        "Name":"Anonymous",
                        "Amount":"00.00",
                        "Message":"Here's A Message",
                        "Created":"2020-10-07T07:14:10.8886913+00:00",
                        "LastUpdated":"2020-10-07T18:13:31.7584897+11:00"
                    },    
                    
                    {
                        "Id":3549476,
                        "Title":"",
                        "Description":"Tax Deductible Donation",
                        "Name":"Josh Day",
                        "Amount":"30.00",
                        "Message":"",
                        "Created":"2020-10-07T07:13:39.6523127+00:00",
                        "LastUpdated":"2020-10-07T18:13:00.4766103+11:00"
                    },

                    {
                        "Id":3549472,
                        "Title":"",
                        "Description":"Tax Deductible Donation",
                        "Name":"Test name 1",
                        "Amount":"00.00",
                        "Message":"",
                        "Created":"2020-10-07T07:13:39.6523127+00:00",
                        "LastUpdated":"2020-10-07T18:13:00.4766103+11:00"
                    },

                    {
                        "Id":3549471,
                        "Title":"",
                        "Description":"Tax Deductible Donation",
                        "Name":"Test name 2",
                        "Amount":"30.00",
                        "Message":"",
                        "Created":"2020-10-07T07:13:39.6523127+00:00",
                        "LastUpdated":"2020-10-07T18:13:00.4766103+11:00"
                    }
                ],
                "ResultsReturned": 2,
                "PageNumber": 1,
                "TotalPages": 1
            }
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