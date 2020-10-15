<template>
    <div class="bd-example-row">
        <div class="bd-example">
            <div class="container">
                <div class="scroller">
                    <a @click="moveDown()" :href="`#stair-${currentStair}`"  class="text-white"><i class="fa fa-2x fa-arrow-down" style="color:white;" aria-hidden="true"></i></a>
                    <a @click="moveUp()" :href="`#stair-${currentStair}`" class="text-white"><i class="fa fa-2x fa-arrow-up" style="color:white;" aria-hidden="true"></i></a>
                </div>
                <div class="stair-container">
                    <Blocks 
                        v-for="(block, i) in sampleData.PaymentDigests"
                        :key="i"
                        :id="`stair-${i + 1}`"
                        :block-status="isEven(i + 1)"
                        :block-items="blockItems"
                        :name="block.Name"
                        :amounts="block.Amount"
                        :block-color="blockColor"
                    />

                </div>
                <pre class="my-5"><code>
                {
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
                </code></pre>
            </div>
        </div>
    </div>
</template>

<script>
import Blocks from './Blocks';

export default {
    name: 'BlocksContainer',
    components: {
        Blocks
    },

    data() {
        return {
            blockColor: '#6e68ff',
            blockItems: 3,
            stairStatus: '',
            stairItems: 1,
            currentStair: 1,
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

    computed: {
        totalBlocks() {
            return this.sampleData.PaymentDigests.length;
        }
    },

    methods: {
        isEven(num) {
            if(num % 2 == 0) {
                return this.stairStatus = 'normal';
            }

            return this.stairStatus = 'flipped'
        },

        moveDown() {
            console.log('down')
            this.sampleData.PaymentDigests.push({});
            console.log(this.sampleData.PaymentDigests);

            this.currentStair++;
            this.stairItems++;
        },

        moveUp() {
            if(this.currentStair === 1) { return; }
            console.log('up');
            this.currentStair--;
            this.stairItems--;
        }
    }

}
</script>

<style lang="scss">
    .stair-container {
        padding-top: 60px;
        scroll-behavior: smooth;
        height: 550px;
        overflow: hidden;
    }

    .scroller {
        position: fixed;
        right: 15%;
        top: 30%;

        a {
            margin-right: 15px;
        }
    }
</style>
